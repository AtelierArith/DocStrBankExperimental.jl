```
function convert_arguments(P::Type{<:AbstractPlot}, arh::AbstractRasterHistogram)
```

Converting method so Makie.jl can plot an `AbstractRasterHistogram`. **Note** for plotting purposes a value correspnding to zero is replaced with `NaN`. This is to avoid in 2D plotting many zero values and as a result not seeing the distribtution clearly (in Makie.kj `heatmap` the `NaN` value is [left out in plotting](https://docs.makie.org/stable/examples/plotting_functions/heatmap/#three_vectors)).
