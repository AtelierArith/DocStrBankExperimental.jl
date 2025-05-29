```
analyze_components!(dataframe::AbstractDataFrame, components::AbstractArray{<:Integer}, f::AbstractComponentAnalysisAlgorithm, args...; kwargs...)
analyze_components!(dataframe::AbstractDataFrame, components::AbstractArray{<:Integer}, fs::Tuple{AbstractComponentAnalysisAlgorithm, Vararg{AbstractComponentAnalysisAlgorithm}}, args...; kwargs...)
```

Analyze connected components using component analysis algorithm `f` or sequence of algorithms specified in a tuple `fs`,  and store the results in a `DataFrame`.

# Output

The information about the components is stored in a `DataFrame`; each row number contains information corresponding to a particular connected component. The `DataFrame` will be changed in place and its columns will store the measurements that algorithm `f` or algorithms `fs` computes.

# Examples

Just simply pass an algorithm to `analyze_components!`:

```julia
df = DataFrame()
f = BasicMeasurement()
analyze_components!(df, components, f)

fs = tuple(RegionEllipse(), Contour())
analyze_components!(df, components, fs)
```

See also: [`analyze_components`](@ref)
