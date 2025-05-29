```
obsview(data, [indices])
```

Return a lazy view of the observations in `data` that correspond to the given `indices`. No data will be copied. 

By default the return is an [`ObsView`](@ref), although this can be overloaded for custom types of `data` that want to provide their own lazy view.

In case `data` is a tuple or named tuple, the constructor will be mapped over its elements. For array types, return a subarray.

The observation in the returned view `ov` can be materialized by calling `getobs(ov, i)` on the view, where `i` is an index in `1:length(ov)`.

If `indices` is not provided, it will be assumed to be `1:numobs(data)`.

# Examples

```jldoctest
julia> obsview([1 2 3; 4 5 6], 1:2)
2×2 view(::Matrix{Int64}, :, 1:2) with eltype Int64:
 1  2
 4  5
```
