```
fastica!(W, X, fun, maxiter, tol, verbose)
```

Invoke the Fast ICA algorithm[^1].

**Parameters:**

  * `W`: The initial un-mixing matrix, of size $(m, k)$. The function updates this matrix inplace.
  * `X`: The data matrix, of size $(m, n)$. This matrix is input only, and won't be modified.
  * `fun`: The approximate neg-entropy functor of type [`ICAGDeriv`](@ref).
  * `maxiter`: Maximum number of iterations.
  * `tol`: Tolerable change of `W` at convergence.

Returns the updated `W`.

**Note:** The number of components is inferred from `W` as `size(W, 2)`.
