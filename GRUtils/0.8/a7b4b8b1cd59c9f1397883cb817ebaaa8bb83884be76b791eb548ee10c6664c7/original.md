```
colorbar(flag::Bool)
colorbar(levels::Integer)
```

Set the color bar of the current plot.

The input argument can be a `Bool` (`true` or `false`) to show or hide the colorbar – if it is available, or an `Integer` to set the number of levels shown in the color bar (256 levels by default).

Color bars are only presented when there is actual color data in the plot, regardless of the usage of this function.

Use the keyword argument `colorbar=<true/false>`, etc. in plotting functions, to enable or disable the color bar during the creation of plots.
