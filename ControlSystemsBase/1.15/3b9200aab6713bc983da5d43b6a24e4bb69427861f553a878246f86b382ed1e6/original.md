```
A, B, C, T = balance_statespace{S}(A::Matrix{S}, B::Matrix{S}, C::Matrix{S}, perm::Bool=false)
sys, T = balance_statespace(sys::StateSpace, perm::Bool=false)
```

Computes a balancing transformation `T` that attempts to scale the system so that the row and column norms of [T*A/T T*B; C/T 0] are approximately equal. If `perm=true`, the states in `A` are allowed to be reordered.

The inverse of `sysb, T = balance_statespace(sys)` is given by `similarity_transform(sysb, T)`

This is not the same as finding a balanced realization with equal and diagonal observability and reachability gramians, see [`balreal`](@ref)
