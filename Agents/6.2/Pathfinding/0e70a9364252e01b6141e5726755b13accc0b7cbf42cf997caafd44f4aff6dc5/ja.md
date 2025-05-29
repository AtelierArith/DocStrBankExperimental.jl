```
move_along_route!(agent, model::ABM{<:ContinuousSpace{D}}, pathfinder::AStar{D}, speed, dt = 1.0)
```

`agent`を指定された`speed`とタイムステップ`dt`で、[`plan_route!`](@ref)によって設定されたターゲットに向かってルートに沿って1ステップ移動させます。

[`ContinuousSpace`](@ref)を持つモデルでの経路探索の場合

エージェントが事前に計算された経路を持っていないか、経路が空の場合、エージェントは静止したままです。
