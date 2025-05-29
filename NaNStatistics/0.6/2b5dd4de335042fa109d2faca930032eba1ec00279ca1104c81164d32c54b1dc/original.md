```julia
histcounts!(N, x, xedges::AbstractRange)
```

Simple 1D histogram; as `histcounts`, but in-place, adding counts to the first `length(xedges)-1` elements of Array `N`.

Note that counts will be added to `N`, not overwrite `N`, allowing you to produce cumulative histograms. However, this means you will have to initialize `N` with zeros before first use.
