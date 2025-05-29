```
addtags[!](siteinds, M::MPS, args...; kwargs...)
addtags[!](siteinds, M::MPO, args...; kwargs...)
```

Apply addtags to all site indices of an MPS/MPO, returning a new MPS/MPO.

The ITensors of the MPS/MPO will be a view of the storage of the original ITensors.
