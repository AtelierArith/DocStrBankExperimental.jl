```
siteinds(commoninds, A::MPO, B::MPS; kwargs...)
siteinds(commonind, A::MPO, B::MPO; kwargs...)
```

Get a vector of the site index (or indices) of MPO `A` that is shared with MPS/MPO `B`.
