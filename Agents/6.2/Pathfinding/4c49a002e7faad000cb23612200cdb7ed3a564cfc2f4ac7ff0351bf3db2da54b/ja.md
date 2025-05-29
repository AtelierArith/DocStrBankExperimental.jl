```
move_along_route!(agent, model::ABM{<:GridSpace{D}}, pathfinder::AStar{D})
```

エージェントを、[`plan_route!`](@ref) によって設定されたターゲットに向かってルートに沿って1ステップ移動させます。

[`GridSpace`](@ref) を持つモデルでの経路探索に使用します。

エージェントが事前に計算された経路を持っていない場合や経路が空の場合、エージェントは静止したままです。
