```
PlannerHeuristic(planner, [d_transform, s_transform])
```

ゴールまでの距離を、`planner`によって返された解に基づいて計算します。

[`OrderedSolution`](@ref)が返された場合、解のコストがヒューリスティック推定値として使用されます（`planner`が[`ForwardPlanner`](@ref)の場合、最終状態のヒューリスティック値が加算されます）。

[`PolicySolution`](@ref)が返された場合、ヒューリスティック推定値として、（[`get_value`](@ref)によって返された）否定値が使用されます。

`d_transform`または`s_transform`が提供されている場合、これは`planner`に渡される入力ドメインまたは状態を変換します。これは、問題を緩和するために使用できます（例：ドメインを単純化する、または状態内の述語を追加/削除することによって）。
