```
deep_eltype(T)
```

返す:

  * `T` が `AbstractArray` コンテナである場合は `deep_eltype`
  * それ以外の場合は `T`

```jldoctest
julia> deep_eltype(Float64)
Float64

julia> deep_eltype(Vector{Float64})
Float64

julia> deep_eltype(Vector{Matrix{Vector{Float64}}})
Float64
```
