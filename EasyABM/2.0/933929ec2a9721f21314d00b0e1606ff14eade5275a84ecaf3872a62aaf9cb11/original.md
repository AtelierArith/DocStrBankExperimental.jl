```julia
neighbor_patches_moore(
    patch::Tuple{Int64, Int64, Int64},
    model::EasyABM.SpaceModel3D{T, S, P<:EasyABM.PeriodicType}
) -> Vector{Tuple{Int64, Int64, Int64}}
neighbor_patches_moore(
    patch::Tuple{Int64, Int64, Int64},
    model::EasyABM.SpaceModel3D{T, S, P<:EasyABM.PeriodicType},
    dist::Int64
) -> Vector{Tuple{Int64, Int64, Int64}}

```

Returns patches neighboring given agent's patch.
