```julia
random_empty_patch(
    model::EasyABM.SpaceModel3D
) -> Union{Nothing, Tuple{Int64, Int64, Int64}}

```

エージェントが存在しないランダムなパッチを返します。そのようなパッチが存在しない場合は何も返しません。
