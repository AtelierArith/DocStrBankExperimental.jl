```julia
nanbinmedian!(M, [N], x, y, xedges::AbstractRange)
```

Fill the array `M` with the medians (and optionally `N` with the counts) of non-NaN `y` values that fall into each of `length(xedges)-1` equally spaced bins along the `x` axis with bin edges specified by `xedges`.

If `y` is a 2-d array (matrix), each column will be treated as a separate variable
