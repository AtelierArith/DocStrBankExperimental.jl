```julia
neighbor_patches_neumann(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D
) -> Vector{Tuple{Int64, Int64, Int64}}
neighbor_patches_neumann(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D,
    dist::Int64
) -> Vector{Tuple{Int64, Int64, Int64}}

```

与えられたパッチに隣接するパッチを返します。
