```
obsv(A, C, n=size(A,1))
obsv(sys, n=sys.nx)
```

Compute the observability matrix with `n` rows for the system described by `(A, C)` or `sys`. Providing the optional `n > sys.nx` returns an extended observability matrix.

Note that checking for observability by computing the rank from `obsv` is not the most numerically accurate way, a better method is checking if `gram(sys, :o)` is positive definite or to call the function [`observability`](@ref).

The unobservable subspace is `nullspace(obsv(A, C))`, initial conditions in this subspace produce a zero response.
