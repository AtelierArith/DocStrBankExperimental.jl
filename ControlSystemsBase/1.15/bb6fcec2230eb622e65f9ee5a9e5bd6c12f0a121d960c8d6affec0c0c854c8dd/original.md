```
ctrb(A, B)
ctrb(sys)
```

Compute the controllability matrix for the system described by `(A, B)` or `sys`.

Note that checking for controllability by computing the rank from `ctrb` is not the most numerically accurate way, a better method is checking if `gram(sys, :c)` is positive definite or to call the function [`controllability`](@ref).

The controllable subspace is given by the range of this matrix, and the uncontrollable subspace is `nullspace(ctrb(A, B)') (note the transpose)`.
