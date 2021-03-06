LightBox for Common Utilities
========

This plugin integrates jQuery ColorBox in XOOPS and [Common Utilities](https://github.com/bitcero/rmcommon).

---

### How to install

1. Download compressed file from [Github!](https://github.com/bitcero/lightbox/)
2. Extract compressend file to your hard disk drive.
3. Upload forlder "lightbox" to directory "modules/rmcommon/plugins" from your XOOPS installation.
4. Go to XOOPS control panel -> Plugins manager and click on tab "available plugins".
5. Install de plugin.
6. Done!

### Configuration
This plugin provides a set of configuration options that can be useful in most of cases. In order to setup the plugin, follow next steps:

1. Go to XOOPS control panel -> Common Utilities block manager.
2. Locate the plugin in the list from "Installed plugins" tab.
3. Click on "settings" option.

Now you can view the configuration form. Modify the values acording to your preferences.

#### Configuration options
Next is the list of available options in Lightbox plugin.

| Option | Default | Posible Values | Description |
|--------|---------|----------------|-------------|
|**Theme**| `Example1` | *Values from list* | This option allows you to change the appearance of plugin |
|**Transition type** | `Elastic` | *Elastic, Fade or None* | Determines the behavior of plugin to adapt to content size |
| **Transition speed** | `350` | *Any positive integer value* | Sets the speed of the fade and elastic transitions, in milliseconds. |
| **Max width** | `90%` | *Any valid value for css property (e.g. 500px, 50%, etc.). Leave **0** for no limit.* | Set a maximum width for loaded content. |
| **Max height** | `90%` | *Any valid value for css property (e.g. 500px, 50%, etc.). Leave **0** for no limit.* | Set a maximum height for loaded content. Example: "100%", 500, "500px". Leave 0 for no limit. |
| **Scale images** | `Yes` | *Yes or No* | If "yes" and if Max width or Max height have been defined, ColorBox will scale photos to fit within the those values. |
| **Loop images** | `No` | *Yes or No* | If "No", will disable the ability to loop back to the beginning of the group when on the last element. |
| **Enable slideshow** | `No` | *Yes or No* | If "Yes", adds an automatic slideshow to a content group / gallery. |
| **Slideshow speed** | `2500` | *Any positive integer value* | Sets the speed of the slideshow, in milliseconds. |
| **Slideshow auto start** | `No` | *Yes or No* | If "Yes", the slideshow will automatic start to play. |
| **Addtitional settings** | `Empty` | *Any other javascript option to pass to jquery plugin* | You can input here any other option that will be passed to jquery plugin declaration. You can view a complete list of available options [here!](http://www.jacklmoore.com/colorbox/) |
---

### How to use
Using LightBox for Common Utilities is very simple.

#### Using custom code
This is the easier way for alls. In order to integrate lighbox with any image (or other elements), you can use the next code:

```
[lightbox]
<a href="#" class="class-name"><img src="thumbnail"></a>
<a ...></a>
...
[/lightbox]
```
#### Passing parameters with custom code
You can pass any valid parameter to jQuery Color box using custom code (Please, check a [list of valid options](http://www.jacklmoore.com/colorbox/)).

```
[lighbox name="lightbox-container" rel="my-thumbnails" transition="fase" scalePhotos="true"]
<a href="#" class="class-name"><img src="my-thumbnails"></a>
<a ...></a>
...
[/lightbox]
```
**Note:** Lighbox will use, in first place, the options than can be configured from settings form. If you specify any of those default values, then the new value provide by ypu will be used.

-----

#### Using with PHP
You can use the plugin directly from your PHP code.

**Example:**

_HTML code:_
```html
<div class="my-thumbnails">
  <a href="image-url-1" class="my-thumb-item" title="The image title"><img src="thumb-url-1"></a>
  <a href="image-url-2" class="my-thumb-item" title="The image title"><img src="thumb-url-2"></a>
  <a href="image-url-3" class="my-thumb-item" title="The image title"><img src="thumb-url-3"></a>
  ...
</div>
```

_PHP code:_
```php
if (RMFunctions::plugin_installed('lightbox')){
  RMLightbox::get()->add_element('.my-thumbnails');
  RMLightbox::get()->render();
}
```

Now, Lighbox will search for a continer with class `my-thumbnails` in HTMl code and will render the apropiate code to display jQuery Colorbox plugin.

#### Passing parameters with PHP

You can pass parameters to javascript code using PHP:

_New PHP code:_
```php
if (RMFunctions::plugin_installed('lightbox')){
  RMLightbox::get()->add_element('.my-thumbnails');
  // Options
  RMLightbox::get()->add_option( 'rel', 'work-image-item' ); // This will show the images as group related for "my-thumb-item" css class
  RMLightbox::get()->add_option( 'transition', 'fade' ); // This will overwrite de default value for "transition" option.
  RMLightbox::get()->render();
}
```
