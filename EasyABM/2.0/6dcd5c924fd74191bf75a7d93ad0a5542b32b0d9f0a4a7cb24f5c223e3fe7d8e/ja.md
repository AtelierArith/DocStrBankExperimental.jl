```julia
neighbor_patches_neumann(
    patch::Tuple{Int64, Int64},
    model::EasyABM.SpaceModel2D{T, S, P<:EasyABM.NPeriodicType}
) -> Vector{Tuple{Int64, Int64}}
neighbor_patches_neumann(
    patch::Tuple{Int64, Int64},
    model::EasyABM.SpaceModel2D{T, S, P<:EasyABM.NPeriodicType},
    dist::Int64
) -> Vector{Tuple{Int64, Int64}}

```

与えられたエージェントのパッチに隣接するパッチを返します。
