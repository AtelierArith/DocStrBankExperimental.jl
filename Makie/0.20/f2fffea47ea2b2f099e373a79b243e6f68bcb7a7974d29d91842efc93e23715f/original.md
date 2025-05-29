```
errorbars(x, y, error_both; kwargs...)
errorbars(x, y, error_low, error_high; kwargs...)
errorbars(x, y, error_low_high; kwargs...)

errorbars(xy, error_both; kwargs...)
errorbars(xy, error_low, error_high; kwargs...)
errorbars(xy, error_low_high; kwargs...)

errorbars(xy_error_both; kwargs...)
errorbars(xy_error_low_high; kwargs...)
```

Plots errorbars at xy positions, extending by errors in the given `direction`.

If you want to plot intervals from low to high values instead of relative errors, use `rangebars`.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.errorbars}` are: 

```
  color         :black
  colormap      :viridis
  colorrange    MakieCore.Automatic()
  colorscale    identity
  cycle         [:color]
  direction     :y
  inspectable   true
  linewidth     1.5
  transparency  false
  visible       true
  whiskerwidth  0
```
