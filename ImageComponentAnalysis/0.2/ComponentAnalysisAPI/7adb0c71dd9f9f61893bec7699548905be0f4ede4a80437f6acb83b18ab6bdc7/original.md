```
analyze_components(components::AbstractArray{<:Integer}, f::AbstractComponentAnalysisAlgorithm, args...; kwargs...)
analyze_components(components::AbstractArray{<:Integer}, f::Tuple{AbstractComponentAnalysisAlgorithm, Vararg{AbstractComponentAnalysisAlgorithm}}, args...; kwargs...)
```

Analyze connected components using algorithm `f` or sequence of algorithms specified in a tuple `fs`, and store the results in a `DataFrame`.

# Output

The information about the components is stored in a `DataFrame`; each row number contains information corresponding to a particular connected component. The columns of the `DataFrame` will store the measurements that algorithm `f` or algorithms `fs` computes.

# Examples

Pass an array of labelled connected components and component analysis algorithm to `analyze_component`.

```julia
f = BasicMeasurement()
analyze_components = analyze_component(components, f)

fs = tuple(RegionEllipse(), Contour())
analyze_components!(df, components, fs)
```

The first example reads as "`analyze_components` of connected `components` using algorithm `f`".

See also [`analyze_components!`](@ref) for appending information about connected components to an existing `DataFrame`.
