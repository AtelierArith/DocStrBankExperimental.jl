```
add_agent_single!(A, model::ABM{<:DiscreteSpace}, properties...; kwargs...)
```

Same as `add_agent!(A, model, properties...; kwargs...)` but ensures that it adds an agent into a position with no other agents (does nothing if no such position exists).
