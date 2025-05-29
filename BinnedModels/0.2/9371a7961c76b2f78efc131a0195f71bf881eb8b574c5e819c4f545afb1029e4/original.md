```
function bin_intervals(edges::BinEdges, closed::Val = Val(:closedleft))::Binning
```

Returns a vector of n bin intervals, derived from a vector of n+1 bin edges.
