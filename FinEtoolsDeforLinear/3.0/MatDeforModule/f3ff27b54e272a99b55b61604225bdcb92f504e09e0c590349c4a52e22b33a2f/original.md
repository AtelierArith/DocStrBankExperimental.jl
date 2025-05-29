```
stressvtot!(::Type{DeforModelRed2DAxisymm}, t::Matrix{T}, v::Vector{T}) where {T}
```

Convert a 4-vector to a  matrix of 3x3 stress components (tensor).

Convert a 4-vector to a *symmetric* matrix of 3x3 stress components (tensor).

The stress vector components need to be ordered as:     sigmax, sigmay, sigmaz, tauxy.
