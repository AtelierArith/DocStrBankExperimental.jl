```
nearest_neighbor(agent, model::ABM{<:ContinuousSpace}, r) → nearest
```

指定された `agent` に最も近い距離を持つエージェントを返します。距離 `r` 内にエージェントが存在しない場合は `nothing` を返します。
