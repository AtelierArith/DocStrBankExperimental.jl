```
siteinds(commoninds, A::MPO, B::MPS, j::Integer; kwargs...)
siteinds(commonind, A::MPO, B::MPO, j::Integer; kwargs...)
```

Get the site index (or indices) of  the `j`th MPO tensor of `A` that is shared with MPS/MPO `B`.
