Plugins for Adminer
===================

## End of life 

⚠️ All these plugins have been integrated into the upcomming [AdminNeo 5](https://github.com/adminneo-org/adminneo) and are no longer compatible with Adminer 5.

## Info

Usefull plugins for **Adminer database tool**.

- [AdminerLoginServers](https://github.com/pematon/adminer-plugins#adminerloginservers)
- [AdminerJsonPreview](https://github.com/pematon/adminer-plugins#adminerjsonpreview)
- [AdminerSimpleMenu](https://github.com/pematon/adminer-plugins#adminersimplemenu)
- [AdminerCollations](https://github.com/pematon/adminer-plugins#adminercollations)
- [How to use](https://github.com/pematon/adminer-plugins#how-to-use)

## Compatibility

- PHP 5.6+
- Adminer 4.4-4.17
- AdminNeo 4.9-4.17

## AdminerLoginServers

Displays constant list of servers in login form. Configuration is similar to the original "login-servers" plugin but – the killer feature – each server can have a different driver!

## AdminerJsonPreview

Displays JSON data as a table.

<img src="http://pematon.github.io/screenshots/json-preview.png" width="728px" />

## AdminerSimpleMenu

Displays only one prefered action in table list.
Get rid of schizophrenic decisions between selecting data and showing table structure. Optimize your workflow!

## AdminerCollations

Allows to set custom character sets in collation select boxes. No more scrolling through 197 options to find utf8mb4_general_ci!

<img src="http://pematon.github.io/screenshots/adminer-collations.png" width="186px" />

## How to use

1. [Download](http://www.adminer.org/#download) and install Adminer tool.

2. Download plugins you want and place them to plugins folder.

File structure will be:
```
- plugins
	- AdminerJsonPreview.php
	- ...
- adminer.php
```

3. Create index.php file and [configure plugins](http://www.adminer.org/plugins/#use).

```php
<?php

	function adminer_object()
	{
		// required to run any plugin
		include_once "./plugins/plugin.php";

		// autoloader
		foreach (glob("plugins/*.php") as $filename) {
			include_once "./$filename";
		}

		$plugins = [
			// specify enabled plugins here
			new AdminerSimpleMenu(),
		];

		return new AdminerPlugin($plugins);
	}

	// include original Adminer or Adminer Editor
	include "./adminer.php";
```

Final file structure will be:
```
- plugins
	- AdminerJsonPreview.php
	- ...
	- plugin.php
- adminer.php
- index.php
```
