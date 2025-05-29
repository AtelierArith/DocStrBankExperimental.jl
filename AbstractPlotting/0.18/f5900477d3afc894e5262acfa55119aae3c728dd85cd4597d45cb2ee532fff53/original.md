```
help_attributes([io], Union{PlotType, PlotFunction}; extended = false)
```

Returns a list of attributes for the plot type `Typ`. The attributes returned extend those attributes found in the `default_theme`.

Use the optional keyword argument `extended` (default = `false`) to show in addition the default values of each attribute. usage:

```example
>help_attributes(scatter)
    alpha
    color
    colormap
    colorrange
    distancefield
    glowcolor
    glowwidth
    linewidth
    marker
    marker_offset
    markersize
    overdraw
    rotations
    strokecolor
    strokewidth
    transform_marker
    transparency
    uv_offset_width
    visible
```
