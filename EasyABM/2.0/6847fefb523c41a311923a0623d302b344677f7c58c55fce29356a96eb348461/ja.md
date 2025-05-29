```julia
neighbors(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType}
) -> Base.Iterators.Filter
neighbors(
    agent::EasyABM.Agent2D,
    model::EasyABM.SpaceModel2D{EasyABM.StaticType},
    dist::Real
) -> Base.Iterators.Filter

```

与えられたエージェントのユークリッド距離 `dist` 内にいるアクティブな隣接エージェントを返します。
