```
plot_path(p1::Plot, lat, lon;
          lab::String        = "",
          Nmax::Int          = 5000,
          show_plot::Bool    = true,
          zoom_plot::Bool    = false,
          path_color::Symbol = :ignore)
```

Plot flight path on an existing plot.

**Arguments:**

  * `p1`:         plot (i.e., map)
  * `lat`:        latitude  [rad]
  * `lon`:        longitude [rad]
  * `lab`:        (optional) data (legend) label
  * `Nmax`:       (optional) maximum number of data points plotted
  * `show_plot`:  (optional) if true, show plot
  * `zoom_plot`:  (optional) if true, zoom plot onto flight path
  * `path_color`: (optional) path color {`:ignore`,`:black`,`:gray`,`:red`,`:orange`,`:yellow`,`:green`,`:cyan`,`:blue`,`:purple`}

**Returns:**

  * `p2`: `p1` with flight path
