```
addtags[!](siteinds, commoninds, M1::MPO, M2::MPS, args...; kwargs...)
addtags[!](siteinds, commoninds, M1::MPO, M2::MPO, args...; kwargs...)
```

Apply addtags to the site indices that are shared by `M1` and `M2`.

Returns new MPSs/MPOs. The ITensors of the MPSs/MPOs will be a view of the storage of the original ITensors.
