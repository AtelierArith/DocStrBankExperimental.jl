```
partial_trace(ρ::State, system::Vector{Int64}, id::Int64) :: State
```

`State` `ρ` の部分トレースを取り、新しい `State` を構築します: $\text{Tr}*B[\rho*{AB}] = \rho*A$。
