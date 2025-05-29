```
prime[!](linkinds, M::MPS, args...; kwargs...)
prime[!](linkinds, M::MPO, args...; kwargs...)
```

Apply prime to all link indices of an MPS/MPO, returning a new MPS/MPO.

The ITensors of the MPS/MPO will be a view of the storage of the original ITensors.
