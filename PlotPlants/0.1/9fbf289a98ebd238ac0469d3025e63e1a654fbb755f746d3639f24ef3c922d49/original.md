```
plot_density!(
            ax::PyObject,
            xs::Array,
            ys::Array;
            cmap::String = "viridis",
            markersize::Number = 8,
            dmax::Number = NaN
)
plot_density!(
            ax::PyObject,
            df::DataFrame;
            cmap::String = "viridis",
            markersize::Number = 8,
            dmax::Number = NaN
)
```

Plot density plot on axis, given

  * `ax` Axis to plot on
  * `xs` Array of X
  * `ys` Array of Y
  * `cmap` Optional. Color map scheme
  * `markersize` Optional. Marker size dimension, scatter size is markersize^2
  * `dmax` Maximal density. If `dmax` is not NaN, use dmax as maximum density
  * `df` A dataframe with column names of ("X","Y","C")
