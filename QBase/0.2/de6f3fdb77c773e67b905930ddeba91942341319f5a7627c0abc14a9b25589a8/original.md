```
partial_trace(ρ::State, system::Vector{Int64}, id::Int64) :: State
```

Takes the partial*trace of a `State` `ρ` to construct a new `State`: ``\text{Tr}*B[\rho*{AB}] = \rho*A``.
