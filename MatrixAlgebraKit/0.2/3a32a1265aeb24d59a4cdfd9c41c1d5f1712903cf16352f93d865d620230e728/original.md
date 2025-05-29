```
left_null(A; [kind::Symbol, trunc, alg_qr, alg_svd]) -> N
left_null!(A, [N]; [kind::Symbol, alg_qr, alg_svd]) -> N
```

Compute an orthonormal basis `N` for the cokernel of the matrix `A` of size `(m, n)`, i.e. the nullspace of `adjoint(A)`, such that `adjoint(A)*N ≈ 0` and `N'*N ≈ I`. The keyword argument `kind` can be used to specify the specific orthogonal decomposition that should be used to factor `A`, whereas `trunc` can be used to control the the rank of `A` via its singular values.

`trunc` can either be a truncation strategy object or a NamedTuple with fields `atol`, `rtol`, and `maxnullity`.

This is a high-level wrapper and will use one of the decompositions `qr!` or `svd!` to compute the orthogonal basis `N`, as controlled by the keyword arguments.

When `kind` is provided, its possible values are

  * `kind == :qr`: `N` is computed using the QR decomposition.   This requires `isnothing(trunc)` and `left_null!(A, [N], kind=:qr)` is equivalent to   `qr_null!(A, [N], alg)` with a default value `alg = select_algorithm(qr_compact!, A; positive=true)`
  * `kind == :svd`: `N` is computed using the singular value decomposition and will contain    the left singular vectors corresponding to either the zero singular values if `trunc`   isn't specified or the singular values specified by `trunc`.

When `kind` is not provided, the default value is `:qr` when `isnothing(trunc)` and `:svd` otherwise. Finally, finer control is obtained by providing an explicit algorithm using the `alg_qr` and `alg_svd` keyword arguments, which will only be used by the corresponding factorization backend. If `alg_qr` or `alg_svd` are NamedTuples, a default algorithm is chosen with `select_algorithm` and the NamedTuple is passed as keyword arguments to that algorithm. `alg_qr` defaults to `(; positive=true)` so that by default a positive QR decomposition will be used.

!!! note
    The bang method `left_null!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `N` as output.


See also [`right_null(!)`](@ref right_null), [`left_orth(!)`](@ref left_orth), [`right_orth(!)`](@ref right_orth)
