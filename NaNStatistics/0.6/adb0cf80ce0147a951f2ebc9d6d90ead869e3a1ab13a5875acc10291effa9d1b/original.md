```julia
histmean(counts, bincenters)
```

Estimate the mean of the data represented by a histogram,  specified as `counts` in equally spaced bins centered at `bincenters`.

## Examples

```julia
julia> binedges = -10:0.01:10;

julia> counts = histcounts(randn(10000), binedges);

julia> bincenters = (binedges[1:end-1] + binedges[2:end])/2
-9.995:0.01:9.995

julia> histmean(counts, bincenters)
0.0039890000000003135
```
