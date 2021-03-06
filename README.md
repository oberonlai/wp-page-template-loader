# PageTemplates
A simple class that allows registering WordPress Page templates from plugins.

## Installation
```
composer require oberonlai/wp-page-template-loader
```

## Usage

It's super simple. Run this somewhere in your WordPress plugin:

```php
<?php
    use ODS\PageTemplateLoader;

    $pageTemplates = new PageTemplateLoader();
    $pageTemplates->addTemplate(
        WP_PLUGIN_DIR . '/my-custom-plugin/templates/template1.php'  => 'templateName1',
        WP_PLUGIN_DIR . '/my-custom-plugin/templates/template2.php'  => 'templateName2',
    );
```

This adds the template to your WordPress site's Page edit interface.
The ``addTemplate()`` function takes one array:

```php

    /**
     * Add a new custom template.
     *
     * @param $template array of file path and template name
     */
    public function addTemplate( Array $template )
    {
        foreach ( $template as $key => $value ) {
            $key = str_replace('\\', '/', $key);
            $this->templates[$key] = $value;
        }
    }
```
## Credits
This library was adapted from http://www.wpexplorer.com/wordpress-page-templates-plugin/
