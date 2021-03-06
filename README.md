# swapnilsarwe/icndb

This package has been moved to [codeat3](https://github.com/codeat3/) namespace with a package name [codeat3/icndb](https://github.com/codeat3/icndb). Please use the alternative package.

A PHP Wrapper for for the [Internet Chuck Norris Database (ICNDb)](http://www.icndb.com).

# Install

To ease the process, I recommend you use [composer](http://getcomposer.org/).

```JSON
{
	"require": {
		"swapnilsarwe/icndb": "1.0.x"
	}
}
```

# Usage

```php
<?php
$config = array(
	'firstName' => 'Cyrus',
	'lastName' => 'David'
);

// Pass an optional parameter to change the firstName and lastName
// Default is Chuck Norris
$chuck = new Swapnilsarwe\ICNDbClient($config);

// Get the total Chuck Norris jokes stored in ICNDb
$total = $chuck->count()->get();

// Get all categories
$categories = $chuck->categories()->get();

// Get a specific joke by it's ID
$specific = $chuck->specific(18)->get();

//Get a random joke
$random = $chuck->random()->get();

// Get multiple random jokes
$random2 = $chuck->random(3)->get();

// use exclude() to get jokes not belong to that category
$exclude = $chuck->random()->exclude('nerdy')->get();

// you can also supply an array
$exclude2 = $chuck->random()->exclude(array('nerdy', 'explicit'))->get();

// or chain them
$exclude3 = $chuck->random(2)->exclude('explicit')->exclude('nerdy')->get();

// use limitTo() to get jokes only from that category
// you may supply an array or chain them like exclude()
$limit = $chuck->random()->limitTo('nerdy')->get();
```

# Exceptions

**APIUnavailableException** - API is either unreachable/unavailable

**ChainNotAllowedException** - When these methods are chained together `random()`, `specific($id)`, `categories()`, `count()`


# Tests

To run the unit test suite:

```
cd tests
curl -s https://getcomposer.org/installer | php
php composer.phar install
./vendor/bin/phpunit
```
