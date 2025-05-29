```julia
histskewness(counts, bincenters)
```

Estimate the skewness of the data represented by a histogram,  specified as `counts` in equally spaced bins centered at `bincenters`.

## Examples

```julia
julia> binedges = -10:0.01:10;

julia> counts = histcounts(randn(10000), binedges);

julia> bincenters = (binedges[1:end-1] + binedges[2:end])/2
-9.995:0.01:9.995

julia> histskewness(counts, bincenters)
0.011075369240851738
```
