```
psceig(A[, k]; fast = false) -> ce
```

Compute the characteristic exponents of a cyclic matrix product of `p` matrices.

Compute the characteristic exponents of a discrete-time periodic matrix `A(t)`. The characteristic exponents are computed from the characteristic multipliers as determined by calling the function [`pseig(::PeriodicMatrix)`](@ref).  If `fast = false` (default) then the characteristic multipliers are computed using an approach based on the periodic Schur decomposition [1], while if `fast = true`  the structure exploiting reduction [2] of an appropriate lifted pencil is employed. This later option may occasionally lead to inaccurate results for large number of matrices. 

The argument `k` specifies the starting index of the component matrices (default: `k = 1`). 

*Note:* The first `nmin` components of `ce` contains the *core characteristic exponents*, where `nmin` is the minimum row dimensions of the component matrices,  while the last components of `ce` are zero. 
