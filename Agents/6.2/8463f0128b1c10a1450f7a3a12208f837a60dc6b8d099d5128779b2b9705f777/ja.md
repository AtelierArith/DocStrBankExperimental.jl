```
random_nearby_agent(agent, model::ABM, r = 1, f = nothing, alloc = false; kwargs...) → agent
```

指定された `agent` の位置の近くにいるランダムなエージェントを返すか、近くにエージェントがいない場合は `nothing` を返します。

引数 `r` の値と可能なキーワードは [`nearby_ids`](@ref) と同様に動作します。

フィルタ関数 `f(agent)` を渡すことで、関数が `true` を返すエージェントのみにサンプリングを制限できます。フィルタリング条件が高コストの場合は、`alloc` 引数を使用できます。この場合、割り当て版の方がパフォーマンスが向上する可能性があります。`f` を満たす近くのエージェントがいない場合は `nothing` が返されます。

離散空間の場合は、指定された位置にいるランダムなエージェントを返すために [`random_agent_in_position`](@ref) を使用してください。
