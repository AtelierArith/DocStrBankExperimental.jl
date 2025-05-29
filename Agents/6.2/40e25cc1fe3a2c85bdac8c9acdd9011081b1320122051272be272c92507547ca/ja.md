```
empty_nearby_positions(pos, model::ABM{<:DiscreteSpace}, r = 1; kwargs...)
empty_nearby_positions(agent, model::ABM{<:DiscreteSpace}, r = 1; kwargs...)
```

指定された位置または指定されたエージェントから半径 `r` 内のすべての空の位置のイテラブルを返します。

`r` の値と可能なキーワードは [`nearby_positions`](@ref) と同様に動作します。
