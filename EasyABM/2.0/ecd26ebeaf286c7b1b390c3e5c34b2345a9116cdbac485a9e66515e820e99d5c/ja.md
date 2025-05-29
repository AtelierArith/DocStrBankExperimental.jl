```julia
neighbors(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.StaticType}
) -> Base.Iterators.Filter
neighbors(
    agent::EasyABM.Agent3D,
    model::EasyABM.SpaceModel3D{EasyABM.StaticType},
    dist::Real
) -> Base.Iterators.Filter

```

与えられたエージェントのユークリッド距離 `dist` 内にいるアクティブな隣接エージェントを返します。
