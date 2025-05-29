```
cardtheme(theme = "grid";
          root = "<current-directory>",
          src = "src",
          destination = "democards") -> templates, stylesheet_path
```

For given theme, return the templates and path to stylesheet.

`root` and `destination` should have the same value to that passed to `makedemos`.

Available themes are:

  * "bulmagrid"
  * "bokehlist"
  * "grid"
  * "list"
  * "nocoverlist"
  * "transitiongrid"
