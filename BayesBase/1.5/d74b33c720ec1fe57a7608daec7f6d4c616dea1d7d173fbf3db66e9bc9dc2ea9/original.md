```
deep_eltype(T)
```

Returns:

  * `deep_eltype` of `T` if `T` is an `AbstractArray` container
  * `T` otherwise

```jldoctest
julia> deep_eltype(Float64)
Float64

julia> deep_eltype(Vector{Float64})
Float64

julia> deep_eltype(Vector{Matrix{Vector{Float64}}})
Float64
```
