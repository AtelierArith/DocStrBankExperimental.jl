```julia
histstd(counts, bincenters; corrected::Bool=true)
```

Estimate the standard deviation of the data represented by a histogram,  specified as `counts` in equally spaced bins centered at `bincenters`.

If `counts` have been normalized, or represent an analytical estimate of a PDF  rather than a histogram representing counts of a dataset, Bessel's correction  to the standard deviation should likely not be performed - i.e., set the  `corrected` keyword argument to `false`. 

## Examples

```julia
julia> binedges = -10:0.01:10;

julia> counts = histcounts(randn(10000), binedges);

julia> bincenters = (binedges[1:end-1] + binedges[2:end])/2
-9.995:0.01:9.995
t
julia> histstd(counts, bincenters)
0.999592620230683
```
