```
plot_path!(p1::Plot, path::Path, ind = trues(path.N);
           lab::String        = "",
           Nmax::Int          = 5000,
           show_plot::Bool    = true,
           zoom_plot::Bool    = false,
           path_color::Symbol = :ignore)
```

Plot flight path on an existing plot.

**Arguments:**

  * `p1`:         plot (i.e., map)
  * `path`:       `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `ind`:        (optional) selected data indices
  * `lab`:        (optional) data (legend) label
  * `Nmax`:       (optional) maximum number of data points plotted
  * `show_plot`:  (optional) if true, show plot
  * `zoom_plot`:  (optional) if true, zoom plot onto flight path
  * `path_color`: (optional) path color {`:ignore`,`:black`,`:gray`,`:red`,`:orange`,`:yellow`,`:green`,`:cyan`,`:blue`,`:purple`}

**Returns:**

  * `nothing`: flight path is plotted on `p1`
