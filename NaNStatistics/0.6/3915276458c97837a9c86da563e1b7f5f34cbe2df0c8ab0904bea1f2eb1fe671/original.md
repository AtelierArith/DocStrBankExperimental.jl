```julia
histkurtosis(counts, bincenters)
```

Estimate the excess kurtosis [1] of the data represented by a histogram,  specified as `counts` in equally spaced bins centered at `bincenters`.

[1] We follow Distributions.jl in returning excess kurtosis rather than raw kurtosis. Excess kurtosis is defined as as kurtosis - 3, such that a Normal distribution has zero excess kurtosis. 

## Examples

```julia
julia> binedges = -10:0.01:10;

julia> counts = histcounts(randn(10000), binedges);

julia> bincenters = (binedges[1:end-1] + binedges[2:end])/2
-9.995:0.01:9.995
t
julia> histkurtosis(counts, bincenters)
0.028863400305099596
```
