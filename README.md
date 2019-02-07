# middlemanTuts
notes on Middleman static site generator

- to initialize Middle project, type the following command in terminal:
    - `middleman init project`
- to view the current project, type the following command in terminal:
    - `middleman server`
    - this will compile all of our files and serve up our project in our default browser, through a local-host

### Folder/Contents
- Source folder
    - where all files, images, static resources, pages, and posts for our website live
    - layouts folder
        - layout.erb file is used as a layout; basically, it's a sekeleton/template that all pages in our project will use
    - index.html.erb
        - the homepage for our entire website
    - confib.rb
        - a ruby file, that has all the main settings for our project, which can be configured from here 
    - Gemfile
        - file used by Ruby, where we can add and specify dependencies, plugins, add-ons, which will be automatically included in our website
    - erb stands for 'embedded ruby'
        - allows us to embed Ruby code inside our HTML and markdown files
        - we can create files without .erb extension, but won't be able to use Ruby code/logic in those files

### Creating and Organizing Content
   - `activate :livereload` in config.rb
   - `gem 'middleman-livereload'` in Gemfile
      - will automatically reload server everytime a change is made to the project
   - finally, `sudo bundle install` in terminal
      - make sure we're in the current directory so that live-reload is included in the project.

### Frontmatter in Middleman
   - information we can store about the content pages on our site, like title, layout, author, language it's written in, etc.
   - for each page on the site, we can have different information about it, then we can access those variables and use them inside our middleman pages/layouts 
   - can be written in two languages
      1) YAML - a langugae used to define key-pair values
         - simple to use and not as syntax-heavy
         - we can access the title of the current page we're on, as stated below
         `<%= current_page.data.title %>`
         - synatx for YAML is as follows:
            `---`
            `title: New Title`
            `---`
      2) JSON - JavaScript Object notation
         - syntax for JSON is as follows:
            `;;;`
            `"title": "New Title"`
            `'''`
      - both of these are interchangable
   - we can access these frontmatter variables on any page that has embedded Ruby, then we can use <%= %> tags and access the information on those embedded Ruby pages
   - the best place to access them would be inside our templates/layouts 

### Helper Methods in Middleman
   - snippets of code you can add to your HTML/markdown file that simplify some common HTML tasks
      - for example, in a md file we don't want to include any ugly/messy HTML; when writing an HTML file, we may not want to go through the trouble of creating links, forms, etc
      - syntax for a helper-method is as follows:
         `<%= [help_method goes here] %>`

### Layouts in Middleman
   - special HTML files (high-level templates) that are used as templates for all the other HTML files on our websites
   - useful if we want all our sites to look the same, but the content to look different 
   - layout.erb is the default layout that comes with middleman
      - it's an HTML skeleton and in the body we have a special `<%= yield %>` tag
         - this tag becomes the placeholder for all the code in the HTML file that we're currently browsing
      - we can create new layouts to be used with other HTML files but they need to be specified in frontmatter using YAML
   - instead of manually specifying which layout to use in front-matter, there's a more powerful/efficient way of doing it through `config.rb`, in one place where all layouts are specified
   - we can also nest templates

### Partials in Middleman
   - special erb/html files where common elements are stored
      - for example, if we want the same header on mutliple layouts, this is where partials come in useful
   - naming convention
      - _partial.erb
      - the underscore in front of the file name is how middleman knows this is a partial

### Data Files
   - inside the data folder, we can store all sorts and types of data, like JSON and YAML
   - when we want to change the data, we can access the files in that folder and change it
   - the data folder sits in the main project folder, as opposed to inside the source folder
   - content in this data folder can be accessed through our layouts, as well as the index.html file
   - we can also loop through the data and list them out

### Conditionals - If Statements
   - conditionals, here, are a way to make our .erb files make decisions, making our layouts smarter
   - if we have a layout in our middleman, we can use conditions (if-else statements) to help it make decisions 
   - meaning, we can use conditionals to display a certain HTML element

### Sitemap Variable
   - sitemap variable is a variable we can use to access all the information about the pages on our website
   - by using sitemap we can loop through all the pages on our website or we can access information about a specific page
      - it can be used to build navigational elements, or 
      - to learn about the actual structure and the place of the current page in our entire directory 
   `<% sitemap.resources.each do |f| %>`
   `<% end %>`
      - what's happening here, is we're looping through all the resources on our site

### Building a blog in middleman
   - By default middleman doesn't assume we want a specific template. If we want to, we need to first install the blog gem to our machine by typing the following command in the terminal
      `gem install middleman-blog`
   - now to create a blog (project), type the following command in the terminal
      `middleman init myBlog --template=blog`
