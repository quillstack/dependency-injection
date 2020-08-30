# Dependency Injection Container

The dependency injection container based on PSR-11: Container interface,
and with the main goal: to be fast.

### Installation

To install this package, run the standard command using _Composer_:

```
composer require quillguild/dependency-injection
```

### Usage

You can use Quill DI when you want:
- To have a simple and fast DI container.
- Define dependencies based on interfaces.
- Define parameters e.g. credentials for a database in `Database` class.

#### Simple usage

You can easily start using a DI Container:

```php
<?php

use QuillDI\Container;

require __DIR__ . '/../vendor/autoload.php';

$container = new Container();
$controller = $container->get(ExampleController::class);
```

#### Dependencies based on interfaces

If you want to define which class should be loaded based on an interface,
you can easily do that:

```php
$container = new Container([
    LoggerInterface::class => Logger::class,
]);
$controller = $container->get(ExampleController::class);
```

#### Dependencies with parameters

If some of your classes require parameters, define them as an array
passed on the second parameter to the container:

```php
$container = new Container([], [
    Database::class => [
        'hostname' => 'localhost',
    ],
]);
$controller = $container->get(ExampleController::class);
```

### Benchmarks

There's a repository where you can see the benchmark results. You can
also do your own tests: \
https://github.com/quillguild/dependency-injection-example

Containers used in these tests:
- Quill DI: https://github.com/quillguild/dependency-injection
- Dice: https://github.com/Level-2/Dice
- PHP-DI: https://github.com/PHP-DI/PHP-DI
- Symfony: https://github.com/symfony/dependency-injection
- Laminas DI: https://github.com/laminas/laminas-di
- Aura.Di: https://github.com/auraphp/Aura.Di
