```
ArnoldiFit
```

A polynomial type produced through fitting a degree $n$ or less polynomial to data $(x_1,y_1),…,(x_N, y_N), N ≥ n+1$, This uses Arnoldi orthogonalization to avoid the exponentially ill-conditioned Vandermonde polynomial. See [`Polynomials.polyfitA`](@ref) for details.

This is useful for polynomial evaluation, but other polynomial operations are not defined. Though these fitted polynomials may be converted to other types, for larger degrees this will prove unstable.
