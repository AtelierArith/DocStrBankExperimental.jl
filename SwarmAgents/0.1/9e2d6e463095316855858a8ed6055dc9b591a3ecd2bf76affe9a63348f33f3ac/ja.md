```
run_full_turn(agent::Agent, messages::AbstractVector{<:PT.AbstractMessage},
    context::Dict{Symbol, Any} = Dict{Symbol, Any}(); max_turns::Int = 5,
    kwargs...)
```

エージェントのフルターンを実行します（すべてのツール呼び出しを実行します）。
