```
F = FeatureArray(data::AbstractArray, features::Union{Tuple{Symbol},Vector{Symbol}}, [timeseries::Union{Vector, Tuple}], args...)
```

Construct a `FeatureArray`, which annotates the array `data` with names of `features` along rows and, optionally, `timeseries` along columns. Since `FeatureArray <: AbstractFeatureArray <: AbstractDimArray`, further arguments to the `FeatureArray` constructor are passed to the `DimArray` constructor. To access feature names, use `getnames(F)`.

# Examples

```julia
data = rand(Int, 2, 10) # Some feature matrix with 2 features and 10 timeseries
F = FeatureArray(data, [:sum, :length])
```
