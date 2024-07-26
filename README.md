# Masar
A lightweight and flexible PHP router with support for dynamic route parameters.

## Features

- Simple and intuitive API
- Support for GET and POST requests
- Dynamic route parameters
- Easy to integrate and extend

## Installation

Clone this repository or download the files:

```bash
git clone https://github.com/yahyamallak/masar.git

```

## Usage

### 1. Basic Setup

```php

require_once dirname(__DIR__) . "/vendor/autoload.php";

use Masar\Http\Request;
use Masar\Routing\Router;

$router = new Router();

// Define routes
$router->get('/', function() {
    echo "Welcome to the homepage!";
});

$router->get('/about', function() {
    echo "About us page";
});

$router->post('/submit', function() {
    echo "Form submitted";
});

// Create a request object
$request = new Request();

// Dispatch the router
try {
    $router->dispatch($request);
} catch (Exception $e) {
    echo '404 Not Found';
}

```

### 2. Using Route Parameters

You can define dynamic segments in your routes using curly braces:


```php

$router->get('/user/{id}', function($id) {
    echo "User profile for user with ID: " . $id;
});

$router->get('/post/{slug}', function($slug) {
    echo "Displaying post: " . $slug;
});

```

### 3. Using Where For Parameters Rules

#### Supported Rules :

- ":digit"
- ":number"
- ":letter"
- ":word"
- ":slug"

```php

$router->get('/user/{id}', function($id) {

    echo "User profile for user with ID: " . $id;

})->where(["id" => ":number"]);

```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open-sourced software licensed under the MIT license.

