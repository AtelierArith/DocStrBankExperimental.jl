```
lognorm(A::MPS)
lognorm(A::MPO)
```

Compute the logarithm of the norm of the MPS or MPO.

This is useful for larger MPS/MPO that are not gauged, where in the limit of large numbers of sites the norm can diverge or approach zero.

See also [`norm`](@ref), [`logdot`](@ref).
