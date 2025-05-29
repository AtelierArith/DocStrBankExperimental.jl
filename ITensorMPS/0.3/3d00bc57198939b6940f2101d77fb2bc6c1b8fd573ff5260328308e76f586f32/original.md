```
addtags[!](siteinds, uniqueinds, M1::MPO, M2::MPS, args...; kwargs...)
```

Apply addtags to the site indices of `M1` that are not shared with `M2`. Returns new MPSs/MPOs.

The ITensors of the MPSs/MPOs will be a view of the storage of the original ITensors.
