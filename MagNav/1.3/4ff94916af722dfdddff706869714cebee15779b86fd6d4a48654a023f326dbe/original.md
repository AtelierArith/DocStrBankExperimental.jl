```
plot_path(lat, lon;
          lab::String        = "",
          dpi::Int           = 200,
          margin::Int        = 2,
          Nmax::Int          = 5000,
          show_plot::Bool    = true,
          zoom_plot::Bool    = true,
          path_color::Symbol = :ignore)
```

Plot flight path.

**Arguments:**

  * `lat`:        latitude  [rad]
  * `lon`:        longitude [rad]
  * `lab`:        (optional) data (legend) label
  * `dpi`:        (optional) dots per inch (image resolution)
  * `margin`:     (optional) margin around plot [mm]
  * `Nmax`:       (optional) maximum number of data points plotted
  * `show_plot`:  (optional) if true, show plot
  * `zoom_plot`:  (optional) if true, zoom plot onto flight path
  * `path_color`: (optional) path color {`:ignore`,`:black`,`:gray`,`:red`,`:orange`,`:yellow`,`:green`,`:cyan`,`:blue`,`:purple`}

**Returns:**

  * `p1`: plot of flight path
