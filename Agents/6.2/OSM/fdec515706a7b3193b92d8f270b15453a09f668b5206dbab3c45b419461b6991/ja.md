```
move_along_route!(agent, model::ABM{<:OpenStreetMapSpace}, distance::Real) → remaining
```

エージェントを計画されたルートに沿って `distance` だけ移動させます。距離の単位は、基盤となるグラフの `weight_type` によって指定されます。提供された `distance` がルートの終点までの距離より大きい場合、残りの距離を返します。そうでない場合は `0` を返します。`is_stationary(agent, model)` が `true` の場合も `0` が返されます。
