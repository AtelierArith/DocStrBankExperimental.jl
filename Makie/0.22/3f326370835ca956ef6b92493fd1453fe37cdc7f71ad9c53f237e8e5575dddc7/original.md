```
hist(values)
```

Plot a histogram of `values`.

## Plot type

The plot type alias for the `hist` function is `Hist`.

## Attributes

**`bar_labels`** =  `nothing`  — *No docs available.*

**`bins`** =  `15`  — Can be an `Int` to create that number of equal-width bins over the range of `values`. Alternatively, it can be a sorted iterable of bin edges.

**`color`** =  `@inherit patchcolor`  — Color can either be:

  * a vector of `bins` colors
  * a single color
  * `:values`, to color the bars with the values from the histogram

**`cycle`** =  `[:color => :patchcolor]`  — *No docs available.*

**`direction`** =  `:y`  — Set the direction of the bars.

**`fillto`** =  `automatic`  — Defines where the bars start.

**`flip_labels_at`** =  `Inf`  — *No docs available.*

**`gap`** =  `0`  — Gap between the bars (see barplot).

**`label_color`** =  `@inherit textcolor`  — *No docs available.*

**`label_font`** =  `@inherit font`  — *No docs available.*

**`label_formatter`** =  `bar_label_formatter`  — *No docs available.*

**`label_offset`** =  `5`  — *No docs available.*

**`label_size`** =  `20`  — *No docs available.*

**`normalization`** =  `:none`  — Allows to normalize the histogram. Possible values are:

  * `:pdf`: Normalize by sum of weights and bin sizes. Resulting histogram  has norm 1 and represents a PDF.
  * `:density`: Normalize by bin sizes only. Resulting histogram represents  count density of input and does not have norm 1. Will not modify the  histogram if it already represents a density (`h.isdensity == 1`).
  * `:probability`: Normalize by sum of weights only. Resulting histogram  represents the fraction of probability mass for each bin and does not have  norm 1.
  * `:none`: Do not normalize.

**`offset`** =  `0.0`  — Adds an offset to every value.

**`over_background_color`** =  `automatic`  — *No docs available.*

**`over_bar_color`** =  `automatic`  — *No docs available.*

**`scale_to`** =  `nothing`  — Allows to scale all values to a certain height. This can also be set to `:flip` to flip the direction of histogram bars without scaling them to a common height.

**`strokecolor`** =  `@inherit patchstrokecolor`  — *No docs available.*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *No docs available.*

**`weights`** =  `automatic`  — Allows to statistically weight the observations.
