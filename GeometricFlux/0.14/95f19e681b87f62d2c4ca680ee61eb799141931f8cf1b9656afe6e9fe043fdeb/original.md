```
DeepSet(ϕ, ρ, aggr=+)
```

Deep set model.

# Arguments

  * `ϕ`: Neural network layer for each input before aggregation.
  * `ρ`: Neural network layer after aggregation.
  * `aggr`: An aggregate function applied to the result of message function. `+`, `-`,

`*`, `/`, `max`, `min` and `mean` are available.

# Examples

```jldoctest
julia> ϕ = Dense(64, 16)
Dense(64 => 16)     # 1_040 parameters

julia> ρ = Dense(16, 4)
Dense(16 => 4)      # 68 parameters

julia> DeepSet(ϕ, ρ)
DeepSet(Dense(64 => 16), Dense(16 => 4), aggr=+)

julia> DeepSet(ϕ, ρ, aggr=max)
DeepSet(Dense(64 => 16), Dense(16 => 4), aggr=max)
```

See also [`WithGraph`](@ref) for training layer with static graph.
