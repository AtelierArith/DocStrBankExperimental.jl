```
FeatureArray{T, 2} where {T}
```

An alias to construct a `FeatureArray` for a flat set of timeseries.

# Examples

```julia
data = rand(Int, 2, 3) # Some feature matrix with 2 features and 3 timeseries
F = FeatureMatrix(data, [:sum, :length], [1, 2, 3])
```
