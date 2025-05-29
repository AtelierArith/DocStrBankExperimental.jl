```
nearby_agents(agent, model::ABM, r = 1; kwargs...) -> agent
```

指定された `agent` の位置に近いエージェントのイテラブルを返します。

引数 `r` の値と可能なキーワードは [`nearby_ids`](@ref) と同様に動作します。
