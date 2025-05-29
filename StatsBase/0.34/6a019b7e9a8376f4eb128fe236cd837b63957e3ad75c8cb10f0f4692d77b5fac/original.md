```
merge(h::Histogram, others::Histogram...)
```

Construct a new histogram by merging `h` with `others`. All histograms must have the same binning, shape of weights and properties (`closed` and `isdensity`). The weights of all histograms are summed up for each bin, the weights of the resulting histogram will have the same type as those of `h`.
