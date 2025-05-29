```
sim[!](siteinds, M::MPS, args...; kwargs...)
sim[!](siteinds, M::MPO, args...; kwargs...)
```

Apply sim to all site indices of an MPS/MPO, returning a new MPS/MPO.

The ITensors of the MPS/MPO will be a view of the storage of the original ITensors.
