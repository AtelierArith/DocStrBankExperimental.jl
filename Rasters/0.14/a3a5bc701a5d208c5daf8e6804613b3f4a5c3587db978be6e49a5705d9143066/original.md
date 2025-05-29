```
Band <: Dimension

Band(val=:)
```

Band [`Dimension`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Dimension) for multi-band rasters.

## Example:

```julia
banddim = Band(10:10:100)
# Or
val = A[Band(1)]
# Or
mean(A; dims=Band)
```
