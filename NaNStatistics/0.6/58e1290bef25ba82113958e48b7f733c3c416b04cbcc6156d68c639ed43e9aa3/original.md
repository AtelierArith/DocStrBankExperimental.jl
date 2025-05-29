```julia
histcounts!(N, x, y, xedges::AbstractRange, yedges::AbstractRange)
```

Simple 2D histogram; as `histcounts`, but in-place, adding counts to the first `length(xedges)-1` columns and the first `length(yedges)-1` rows of `N` elements of Array `N`.

Note that counts will be added to `N`, not overwrite `N`, allowing you to produce cumulative histograms. However, this means you will have to initialize `N` with zeros before first use.
