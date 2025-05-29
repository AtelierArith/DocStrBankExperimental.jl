```
hist(values; bins = 15, normalization = :none)
```

Plot a histogram of `values`. `bins` can be an `Int` to create that number of equal-width bins over the range of `values`. Alternatively, it can be a sorted iterable of bin edges. The histogram can be normalized by setting `normalization`. Possible values are:

  * `:pdf`: Normalize by sum of weights and bin sizes. Resulting histogram  has norm 1 and represents a PDF.
  * `:density`: Normalize by bin sizes only. Resulting histogram represents  count density of input and does not have norm 1. Will not modify the  histogram if it already represents a density (`h.isdensity == 1`).
  * `:probability`: Normalize by sum of weights only. Resulting histogram  represents the fraction of probability mass for each bin and does not have  norm 1.
  * `:none`: Do not normalize.

Statistical weights can be provided via the `weights` keyword argument.

The following attributes can move the histogram around, which comes in handy when placing multiple histograms into one plot:

  * `offset = 0.0`: adds an offset to every value
  * `fillto = 0.0`: defines where the bar starts
  * `scale_to = nothing`: allows to scale all values to a certain height
  * `flip = false`: flips all values

Color can either be:

  * a vector of `bins` colors
  * a single color
  * `:values`, to color the bars with the values from the histogram

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.hist}` are: 

```
  bar_labels             "nothing"
  bins                   15
  color                  RGBA{Float32}(0.0f0,0.0f0,0.0f0,0.6f0)
  cycle                  [:color => :patchcolor]
  fillto                 MakieCore.Automatic()
  flip_labels_at         Inf
  label_color            :black
  label_font             :regular
  label_formatter        Makie.bar_label_formatter
  label_offset           5
  label_size             20
  normalization          :none
  offset                 0.0
  over_background_color  MakieCore.Automatic()
  over_bar_color         MakieCore.Automatic()
  scale_to               "nothing"
  weights                MakieCore.Automatic()
```
