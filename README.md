# drupal-module-rebuild
"Rebuild" module for Drupal 6

The Rebuild Module is a simple module aimed at developers and system administrators. It provides an administration page that has buttons that clear or rebuild various Drupal internal data structures.

Main features are:

* Rebuild the Menu System data structures ({menu_router} and {menu_links} database tables)
* Rebuild the Theme system data structures
* Clear cache entries (either a specific CID or the whole cache, including permanent entries, from any, or all, of the cache tables)
* Clear one's own PHP session ($_SESSION) information (this leaves the session in place, but clears all information within it)

The main use for this module is the ability to have Drupal rebuild or clear data structures that may not be relevent after making code changes to modules. During the development of modules, it is often necessary to change menu system configuration (for example), which requires some internal data structures to be rebuilt before these changes take effect. With Drupal 6, this requires a PHP call to menu_rebuild(), rather than simply clearing the {cache_menu} table (as with Drupal 5). This module provides a convienent way to call API functions such as this when required.

You need this module if:

* If you make changes to the hook_menu() function in any module you're working on
* If you make changes to the hook_theme() function in any modules you're working on
* If you have cached data that you need to artifically expire or remove to test your code
* If you have data stored in $_SESSION you need to clear

**This module is potentially dangerous. Whilst cache and menu data is rebuilt dynamically, manipulating these data structures may cause unexpected results and so should not be performed except by advanced users under known circumstances. It's generally not advisable on a live site, for example. Use at your own risk.**
