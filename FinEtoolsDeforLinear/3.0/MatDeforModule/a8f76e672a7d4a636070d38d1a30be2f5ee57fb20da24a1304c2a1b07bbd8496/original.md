```
stressvtot!(::Type{DeforModelRed2DStrain}, t::Matrix{T}, v::Vector{T}) where {T}
```

Convert a vector to a  matrix of 2x2 stress components (symmetric tensor).

If `v` has 4 entries, also the `t[3,3]` matrix entry is set.

The stress vector components need to be ordered as:     sigmax, sigmay, tauxy, sigmaz, which is the ordering used for the plane-strain model reduction.
