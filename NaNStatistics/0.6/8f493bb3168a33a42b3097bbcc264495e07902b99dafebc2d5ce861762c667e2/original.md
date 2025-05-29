```julia
nanbinmean(x, y, xedges::AbstractRange)
```

Ignoring `NaN`s, calculate the weighted mean of `y` values that fall into each of `length(xedges)-1` equally spaced bins along the `x` axis with bin edges specified by `xedges`.

The array of `x` data should given as a one-dimensional array (any subtype of AbstractVector) and `y` as either a 1-d or 2-d array (any subtype of AbstractVecOrMat). If `y` is a 2-d array, then each column of `y` will be treated as a separate variable.
