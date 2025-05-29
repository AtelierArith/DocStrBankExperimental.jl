```
stephist(values)
```

Plot a step histogram of `values`.

## Plot type

The plot type alias for the `stephist` function is `StepHist`.

## Attributes

**`bins`** =  `15`  — Can be an `Int` to create that number of equal-width bins over the range of `values`. Alternatively, it can be a sorted iterable of bin edges.

**`color`** =  `@inherit patchcolor`  — *No docs available.*

**`cycle`** =  `[:color => :patchcolor]`  — *No docs available.*

**`linestyle`** =  `:solid`  — *No docs available.*

**`linewidth`** =  `@inherit linewidth`  — *No docs available.*

**`normalization`** =  `:none`  — Allows to apply a normalization to the histogram. Possible values are:

  * `:pdf`: Normalize by sum of weights and bin sizes. Resulting histogram has norm 1 and represents a PDF.
  * `:density`: Normalize by bin sizes only. Resulting histogram represents count density of input and does not have norm 1. Will not modify the histogram if it already represents a density (`h.isdensity == 1`).
  * `:probability`: Normalize by sum of weights only. Resulting histogram represents the fraction of probability mass for each bin and does not have norm 1.
  * `:none`: Do not normalize.

**`scale_to`** =  `nothing`  — Allows to scale all values to a certain height.

**`weights`** =  `automatic`  — Allows to provide statistical weights.
