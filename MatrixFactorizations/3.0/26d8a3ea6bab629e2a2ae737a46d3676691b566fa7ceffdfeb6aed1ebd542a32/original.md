```
polar(A; algorithm::Symbol, maxiter, tol, verbose)
```

Compute the polar decomposition of the matrix `A`.

Returns a [`PolarDecomposition`](@ref).

Arguments:

`algorithm` (default: `:newton`) may be one of:

  * $:newton$: scaled Newton's method
  * $:qdwh$: the QR-based Dynamically weighted Halley (QDWH) method
  * $:halley$: Halley's method
  * $:schulz$: the Newton Schulz method
  * $:hybrid$: a hybrid Newton method
  * $:svd$: the SVD method

`maxiter` defaults to 100; `tol` defaults to `∛eps(t)`; `verbose` defaults to `false`.
