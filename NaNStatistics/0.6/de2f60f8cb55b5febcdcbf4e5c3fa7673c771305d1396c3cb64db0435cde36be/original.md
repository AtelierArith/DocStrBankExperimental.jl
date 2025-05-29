```julia
nanbinmean!(MU, [N], x, y, xedges::AbstractRange)
```

Ignoring `NaN`s, fill the array `MU` with the means (and optionally `N` with the counts) of non-NAN `y` values that fall into each of `length(xedges)-1` equally spaced bins along the `x` axis with bin edges specified by `xedges`.

The array of `x` data should given as a one-dimensional array (any subtype of AbstractVector) and `y` as either a 1-d or 2-d array (any subtype of AbstractVecOrMat).

The output arrays `MU` and `N` must be the same size, and must have the same number of columns as `y`; if `y` is a 2-d array (matrix), then each column of `y` will be treated as a separate variable.
