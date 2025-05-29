```
siteinds(uniqueinds, A::MPO, B::MPS, j::Integer; kwargs...)
siteinds(uniqueind, A::MPO, B::MPS, j::Integer; kwargs...)
```

Get the site index (or indices) of MPO `A` that is unique to `A` (not shared with MPS/MPO `B`).
