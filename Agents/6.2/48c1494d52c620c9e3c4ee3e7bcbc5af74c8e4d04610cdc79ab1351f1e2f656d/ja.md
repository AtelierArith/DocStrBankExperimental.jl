```
add_agent_single!(A, model::ABM{<:DiscreteSpace}, properties...; kwargs...)
```

`add_agent!(A, model, properties...; kwargs...)` と同様ですが、他のエージェントが存在しない位置にエージェントを追加することを保証します（そのような位置が存在しない場合は何もしません）。
