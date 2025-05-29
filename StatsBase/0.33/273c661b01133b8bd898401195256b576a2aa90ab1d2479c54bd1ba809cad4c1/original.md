```
normalize(h::Histogram{T,N}; mode::Symbol=:pdf) where {T,N}
```

Normalize the histogram `h`.

Valid values for `mode` are:

  * `:pdf`: Normalize by sum of weights and bin sizes. Resulting histogram  has norm 1 and represents a PDF.
  * `:density`: Normalize by bin sizes only. Resulting histogram represents  count density of input and does not have norm 1. Will not modify the  histogram if it already represents a density (`h.isdensity == 1`).
  * `:probability`: Normalize by sum of weights only. Resulting histogram  represents the fraction of probability mass for each bin and does not have  norm 1.
  * `:none`: Leaves histogram unchanged. Useful to simplify code that has to  conditionally apply different modes of normalization.

Successive application of both `:probability` and `:density` normalization (in any order) is equivalent to `:pdf` normalization.
