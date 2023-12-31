# ![DevOn App]
 
> ### Laravel codebase containing Devon Ecommerce (Product listing with filters and details page with rating and review)  

This repo is functionality complete — PRs and issues welcome!

----------

# Getting started

## Installation

Please check the official laravel installation guide for server requirements before you start. [Official Documentation](https://laravel.com/docs/8.x/installation)

Alternative installation is possible without local dependencies relying on [Docker](#docker). 

Clone the repository

    git clone https://github.com/vivek0460/devon.git

Switch to the repo folder

    cd devon

Install all the dependencies using composer

    composer install

Install all the dependencies using npm

    npm install

Copy the example env file and make the required configuration changes in the .env file

    cp .env.example .env

Generate a new application key

    php artisan key:generate

Run the database migrations (**Set the database connection in .env before migrating**)

    php artisan migrate

Setup nginx/apache config for subdomain setup on localhost like devon.localhost

    http://devon.localhost

Set proper permission to storage dir

    sudo chmod -R 0777 storage

Start npm to run vuejs

    npm run watch

Run the test cases

    php artisan test

You can now access the server at http://devon.localhost

**TL;DR command list**

    git clone https://github.com/vivek0460/Devon.git
    cd Devon
    composer install
    cp .env.example .env
    php artisan key:generate
    php artisan jwt:generate 
    
**Make sure you set the correct database connection information before running the migrations** [Environment variables](#environment-variables)

    php artisan migrate 

## Database seeding

**Populate the database with seed data with relationships which includes users, products, categories, product_images etc This can help you to quickly start testing the api or couple a frontend and start using it with ready content.**

Run the database seeder and you're done

    php artisan db:seed

***Note*** : It's recommended to have a clean database before seeding. You can refresh your migrations at any point to clean the database by running the following command

    php artisan migrate:refresh
    
  
The api can be accessed at [http://devon.localhost/api/v1](http://devon.localhost/api/v1).

## API Specification

This application adheres to the api specifications set by the [Vivek0460](https://github.com/vivek0460) team. This helps mix and match any backend with any other frontend without conflicts.
  
More information regarding the project can be found here https://github.com/vivek0460/devon.git

----------

# Code overview

## Dependencies

- [darkaonline/l5-swagger](https://zircote.github.io/swagger-php) - For Swagger
- [laravel-cors](https://github.com/barryvdh/laravel-cors) - For handling Cross-Origin Resource Sharing (CORS)

## Folders

- `app` - Contains all the Eloquent models
- `app/Http/Controllers/ProductCOntroller` - Contains all the api controllers for products
- `app/Http/Middleware` - Contains the JWT auth middleware
- `app/Http/Requests` - Contains all the api form requests
- `config` - Contains all the application configuration files
- `database/factories` - Contains the model factory for all the models
- `database/migrations` - Contains all the database migrations
- `database/seeds` - Contains the database seeder
- `routes` - Contains all the api routes defined in api.php file
- `tests` - Contains all the application tests
- `tests/Feature/Api` - Contains all the api tests

## Environment variables

- `.env` - Environment variables can be set in this file

***Note*** : You can quickly set the database information and other variables in this file and have the application fully working.

----------

# Testing API

Run the laravel development server

    php artisan test

The api can now be accessed at

    http://devon.localhost/api

Swagger API documentation
    
    http://devon.localhost/api/documentation#/default

Request headers

| **Required**  | **Key**               | **Value**             |
|---------- |------------------ |------------------ |
| Yes       | Content-Type      | application/json  |
| Yes       | X-Requested-With  | XMLHttpRequest    |
| Optional  | Authorization     | Token {JWT}       |

Refer the [api specification](#api-specification) for more info.

----------
# Repo pattern
Not used in this application, but we can create contract class and abstract classes in case we are working on real application


# Authentication
 
No Auth Needed for current requirments

----------

# Cross-Origin Resource Sharing (CORS)
 
This applications has CORS enabled by default on all API endpoints. The default configuration allows requests from `http://localhost:3000` and `http://localhost:4200` to help speed up your frontend testing. The CORS allowed origins can be changed by setting them in the config file. Please check the following sources to learn more about CORS.
 
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS
- https://en.wikipedia.org/wiki/Cross-origin_resource_sharing
- https://www.w3.org/TR/cors

