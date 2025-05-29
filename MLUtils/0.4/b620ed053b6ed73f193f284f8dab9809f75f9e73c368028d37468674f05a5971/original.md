```
obsview(data::AbstractArray, [obsdim])
obsview(data::AbstractArray, idxs, [obsdim])
```

Return a view of the array `data` that correspond to the given indices `idxs`. If `obsdim` of type [`ObsDim`](@ref) is provided, the observation  dimension of the array is assumed to be along that dimension, otherwise it is assumed to be the last dimension.

If `idxs` is not provided, it will be assumed to be `1:numobs(data)`.

# Examples

```jldoctest
julia> x = rand(4, 5, 2);

julia> v = obsview(x, 2:3, ObsDim(2));

julia> numobs(v)
2

julia> getobs(v, 1) == x[:, 2, :]
true

julia> getobs(v, 1:2) == x[:, 2:3, :]
true
```
