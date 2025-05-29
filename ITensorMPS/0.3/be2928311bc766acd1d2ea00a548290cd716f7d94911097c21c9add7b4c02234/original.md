```
removetags[!](siteinds, M::MPS, args...; kwargs...)
removetags[!](siteinds, M::MPO, args...; kwargs...)
```

Apply removetags to all site indices of an MPS/MPO, returning a new MPS/MPO.

The ITensors of the MPS/MPO will be a view of the storage of the original ITensors.
