```
setprime[!](linkinds, M::MPS, args...; kwargs...)
setprime[!](linkinds, M::MPO, args...; kwargs...)
```

Apply setprime to all link indices of an MPS/MPO, returning a new MPS/MPO.

The ITensors of the MPS/MPO will be a view of the storage of the original ITensors.
