```
rq(A) -> F
```

Compute the RQ factorization of the matrix `A`: an orthogonal/unitary matrix `Q` and and upper triangular or trapezoidal matrix `R` such that

$$
A = [0 R] Q
$$

The returned object `F` stores the factorization in a packed format [`RQ`](@ref). Unlike the `QR` factorization this does not handle least squares problems. If `A` is `m`×`n` then `Q` is `n`×`n` and `R` is `m`×`min(m,n)`.
