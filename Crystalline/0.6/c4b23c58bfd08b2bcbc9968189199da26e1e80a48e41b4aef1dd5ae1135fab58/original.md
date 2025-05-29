```
SymmetryVectors(
    nvs :: AbstractVector{<:Integer},
    irlabs_nv :: AbstractVector{<:AbstractString},
    lgirsd :: AbstractDict{String, <:AbstractVector{LGIrrep{D}}}) 
                                                        --> Vector{SymmetryVector{D}}
```

Similar to [`SymmetryVector(::AbstractVector{<:Integer}, ::AbstractVector{<:AbstractString}, ::AbstractDict)](@ref), but for a vector of distinct raw multiplicy vectors `nvs`, rather than a single vector, returning a `Vector{SymmetryVector{D}}`.

The returned `SymmetryVector`s, `ns`, will share the same underlying irrep information such that `irreps(n) === irreps(n′)` for all `n` and `n′` in `ns`.
