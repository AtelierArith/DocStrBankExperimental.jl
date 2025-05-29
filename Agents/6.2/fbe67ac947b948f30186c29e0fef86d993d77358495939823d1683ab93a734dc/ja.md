```
move_agent_single!(agent, model::ABM{<:DiscreteSpace}; cutoff) → agent
```

エージェントをランダムな位置に移動させますが、位置ごとに最大1つのエージェントのみを尊重します。空いている位置がない場合、エージェントは移動しません。

キーワード `cutoff = 0.998` は [`random_empty`](@ref) に送信されます。
