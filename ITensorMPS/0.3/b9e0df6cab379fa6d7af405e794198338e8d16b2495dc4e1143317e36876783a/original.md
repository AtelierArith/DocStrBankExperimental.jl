```
settags[!](M::MPS, args...; kwargs...)
settags[!](M::MPO, args...; kwargs...)
```

Apply settags to all ITensors of an MPS/MPO, returning a new MPS/MPO.

The ITensors of the MPS/MPO will be a view of the storage of the original ITensors. Alternatively apply the function in-place.
