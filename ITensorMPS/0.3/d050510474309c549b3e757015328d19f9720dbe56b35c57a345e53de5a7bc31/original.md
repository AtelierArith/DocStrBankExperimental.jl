```
noprime[!](linkinds, M::MPS, args...; kwargs...)
noprime[!](linkinds, M::MPO, args...; kwargs...)
```

Apply noprime to all link indices of an MPS/MPO, returning a new MPS/MPO.

The ITensors of the MPS/MPO will be a view of the storage of the original ITensors.
