# LAMP Development Environment

A LAMP development environment stack, built with Docker Compose, containing: 
- PHP (7.4.x, 8.0.x, 8.1.x)
- Apache
- MySQL/MariaDB
- phpMyAdmin
- Redis
- Mailhog
- Xdebug

 
##  Installation
- Clone this repo on your local machine
- Create a .env (copy from `sample.env`) and configure it as needed 
- Run `docker-compose up --detach` from withing the project's folder.
```shell
  git clone git@github.com:shimango/lamp lamp
  cd lamp/
  
  // Copy and modify sample.env as needed
  cp sample.env .env
    
  docker-compose up --detach
```
If everything went okay the LAMP development environment should be up and running. To test it, access
`http://dev.test.localhost` and you should see a phpinfo page.

## Usage
A dynamic virtual host and dns setup is provided so no extra configuration is needed. Create your projects withing the 
`www` folder and make sure your index.php file is in a sub-folder. Setting your project this way, all you need to do now 
is to go to access your site using the address pattern `dev.{folder}.{subfolder}.localhost` on your browser. 
For example:
- `./www/drupal/web/index.php` can be accessed at http://dev.drupal.web.localhost
- `./www/symfony/public/index.php` can be accessed at http://dev.symphony.public.localhost
- `./www/myproject/html/index.php` can be accessed at http://dev.myproject.html.localhost

A self-signed certificates is set for the dynamic virtual hosts so all sites can be accessed using `https`. Because I 
wanted it to be as easy as possible to fire up a new project and start developing, and didn't want to have to manually 
set much at all, there's a single certificate shared across all dynamic sites. However, static virtual hosts can be set
by adding then to `./config/vhosts` 