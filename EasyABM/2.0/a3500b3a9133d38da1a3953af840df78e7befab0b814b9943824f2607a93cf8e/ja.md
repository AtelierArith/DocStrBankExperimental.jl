```julia
neighbor_patches_neumann(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D
) -> Vector{Tuple{Int64, Int64}}
neighbor_patches_neumann(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D,
    dist::Int64
) -> Vector{Tuple{Int64, Int64}}

```

与えられたパッチに隣接するパッチを返します。
