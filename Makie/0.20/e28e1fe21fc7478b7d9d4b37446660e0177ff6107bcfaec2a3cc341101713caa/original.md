```
stephist(values; bins = 15, normalization = :none)
```

Plot a step histogram of `values`. `bins` can be an `Int` to create that number of equal-width bins over the range of `values`. Alternatively, it can be a sorted iterable of bin edges. The histogram can be normalized by setting `normalization`.

Shares most options with `hist` plotting function.

Statistical weights can be provided via the `weights` keyword argument.

The following attributes can move the histogram around, which comes in handy when placing multiple histograms into one plot:

  * `scale_to = nothing`: allows to scale all values to a certain height

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.stephist}` are: 

```
  bins           15
  color          RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  cycle          [:color => :patchcolor]
  linestyle      :solid
  normalization  :none
  scale_to       "nothing"
  weights        MakieCore.Automatic()
```
