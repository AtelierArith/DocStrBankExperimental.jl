```
norm(A::MPS)
norm(A::MPO)
```

Compute the norm of the MPS or MPO.

If the MPS or MPO has a well defined orthogonality center, this reduces to the norm of the orthogonality center tensor. Otherwise, it computes the norm with the full inner product of the MPS/MPO with itself.

See also [`lognorm`](@ref).
