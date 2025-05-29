```
FeatureArray{T, 1} where {T}
```

An alias to construct a `FeatureArray` for a single time series.

# Examples

```julia
data = randn(2) # Feature values for 1 time series
𝐟 = FeatureVector(data, [:sum, :length])
```
