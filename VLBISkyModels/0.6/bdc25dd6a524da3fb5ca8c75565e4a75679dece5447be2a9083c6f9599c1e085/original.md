```
MRing(c::Union{NTuple{N, <:Complex}, AbstractVector{<:Complex}})
```

Construct an MRing geometric model from a complex vector `c` that correspond to the real and imaginary (or cos and sin) coefficients of the Fourier expansion. The `N` in the type defines the order of the Fourier expansion.
