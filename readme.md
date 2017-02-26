
# Composer Assets Plugin

Composer plugin for installing assets.


## Installation

Use [Composer](http://getcomposer.org/):

```
composer require frontpack/composer-assets-plugin
```

Library requires PHP 5.4.0 or later.


## Commands

* `composer refresh-assets` - refresh files in `assets` directory


## Assets configuration

### Packages

* `assets-files` in section `extra`
	* `true` - symlinks whole package directory
	* file path - symlinks one file or directory
	* list of file paths - symlinks files/directories

Example:

``` json
{
	"extra": {
		"assets-files": [
			"static/plugin.js",
			"static/plugin.css",
			"static/icons.png"
		]
	}
}
```

* `static/plugin.js` - symlinks file to `assets/org/package/plugin.js`
* `static/plugin.css` - symlinks file to `assets/org/package/plugin.css`
* `static/icons.png` - symlinks file to `assets/org/package/icons.png`


### Root package

* `assets-dir` - directory for installing of assets, default `assets`, relative to `vendor-dir`
* `assets-directory` - alias for `assets-dir`
* `assets-files` - list of asset files in incompatible packages, it overrides `assets-files` from installed packages
* `assets-strategy` - install strategy for assets
	* `auto` - select strategy by platform (default value)
	* `copy` - copy all assets, default strategy on Windows
	* `symlink` - create relative symlinks, default strategy on non-Windows platforms

Example:

``` json
{
	"config": {
		"assets-dir": "public",
		"assets-files": {
			"org/package": true,
			"org/package2": "js/calendar.js",
			"org/package3": [
				"static/plugin.js",
				"static/plugin.css",
				"static/icons.png"
			]
		}
	}
}
```

* `org/package` - symlinks whole package directory to `public/org/package`
* `org/package2` - symlinks file `js/calendar.js` to `public/org/package2/calendar.js`
* `org/package3`
	* `static/plugin.js` - symlinks file to `public/org/package3/plugin.js`
	* `static/plugin.css` - symlinks file to `public/org/package3/plugin.css`
	* `static/icons.png` - symlinks file to `public/org/package3/icons.png`


## Default mapping

Plugin provides default mapping for selected incompatible packages. You can override this mapping in your `composer.json`.

List of packages with default mapping:

* `components/jquery`
* `nette/forms`
* `o5/grido`

------------------------------

License: [New BSD License](license.md)
<br>Author: Jan Pecha, https://www.janpecha.cz/
