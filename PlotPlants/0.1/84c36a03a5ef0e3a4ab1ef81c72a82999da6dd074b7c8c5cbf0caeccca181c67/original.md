```
plot_hexbin!(
            ax::PyObject,
            xs::Array,
            ys::Array;
            cmap::String = "Greys",
            logbins::Bool = false,
            gridsize::Number = 25
)
plot_hexbin!(
            ax::PyObject,
            xs::Array,
            ys::Array,
            xlims::Array,
            ylims::Array;
            cmap::String = "Greys",
            logbins::Bool = false,
            gridsize::Number = 25
)
```

Plot density plot on axis, given

  * `ax` Axis to plot on
  * `xs` Array of X
  * `ys` Array of Y
  * `cmap` Optional. Color map scheme
  * `logbins` Optional. If true, use log(count) to color the bins
  * `gridsize` Number of bins on both directions
  * `xlim` Limits of x axis. Used to make plot region equal among subplots
  * `ylim` Limits of y axis. Used to make plot region equal among subplots
