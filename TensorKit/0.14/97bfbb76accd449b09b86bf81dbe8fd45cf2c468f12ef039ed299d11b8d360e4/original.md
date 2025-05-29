```
allind(::Union{TT,Type{TT}}) where {TT<:AbstractTensorMap} -> Tuple{Int}
```

Return all indices of a tensor, i.e. the indices of its domain and codomain.

See also [`codomainind`](@ref) and [`domainind`](@ref).
