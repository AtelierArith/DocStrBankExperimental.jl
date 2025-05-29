```
ecdfplot(values; npoints=10_000[, weights])
```

Plot the empirical cumulative distribution function (ECDF) of `values`.

`npoints` controls the resolution of the plot. If `weights` for the values are provided, a weighted ECDF is plotted.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.ecdfplot}` are: 

```
  alpha           1.0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color]
  depth_shift     0.0f0
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  space           :data
  ssao            false
  step            :pre
  transparency    false
  visible         true
```
