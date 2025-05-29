```
andrewsplot(args...; kw...)
```

Shows each row of an array (or table) as a line. The `x` argument specifies a grouping variable. This is a way to visualize structure in high-dimensional data. https://en.wikipedia.org/wiki/Andrews_plot #Examples

```julia
using RDatasets, StatsPlots
iris = dataset("datasets", "iris")
@df iris andrewsplot(:Species, cols(1:4))
```
