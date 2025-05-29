```
rangebars(val, low, high; kwargs...)
rangebars(val, low_high; kwargs...)
rangebars(val_low_high; kwargs...)
```

Plots rangebars at `val` in one dimension, extending from `low` to `high` in the other dimension given the chosen `direction`.

If you want to plot errors relative to a reference value, use `errorbars`.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.rangebars}` are: 

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
