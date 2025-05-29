```
right_null(A; [kind::Symbol, alg_lq, alg_svd]) -> Nᴴ
right_null!(A, [Nᴴ]; [kind::Symbol, alg_lq, alg_svd]) -> Nᴴ
```

Compute an orthonormal basis `N = adjoint(Nᴴ)` for the kernel or nullspace of the matrix `A` of size `(m, n)`, such that `A*adjoint(Nᴴ) ≈ 0` and `Nᴴ*adjoint(Nᴴ) ≈ I`. The keyword argument `kind` can be used to specify the specific orthogonal decomposition that should be used to factor `A`, whereas `trunc` can be used to control the the rank of `A` via its singular values.

`trunc` can either be a truncation strategy object or a NamedTuple with fields `atol`, `rtol`, and `maxnullity`.

This is a high-level wrapper and will use one of the decompositions `lq!` or `svd!` to compute the orthogonal basis `Nᴴ`, as controlled by the keyword arguments.

When `kind` is provided, its possible values are

  * `kind == :lq`: `Nᴴ` is computed using the (nonpositive) LQ decomposition.   This requires `isnothing(trunc)` and `right_null!(A, [Nᴴ], kind=:lq)` is equivalent to   `lq_null!(A, [Nᴴ], alg)` with a default value `alg = select_algorithm(lq_compact!, A; positive=true)`
  * `kind == :svd`: `N` is computed using the singular value decomposition and will contain    the left singular vectors corresponding to the singular values that   are smaller than `max(atol, rtol * σ₁)`, where `σ₁` is the largest singular value of `A`.

When `kind` is not provided, the default value is `:lq` when `isnothing(trunc)` and `:svd` otherwise. Finally, finer control is obtained by providing an explicit algorithm using the `alg_lq` and `alg_svd` keyword arguments, which will only be used by the corresponding factorization backend. If `alg_lq` or `alg_svd` are NamedTuples, a default algorithm is chosen with `select_algorithm` and the NamedTuple is passed as keyword arguments to that algorithm. `alg_lq` defaults to `(; positive=true)` so that by default a positive LQ decomposition will be used.

!!! note
    The bang method `right_null!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `Nᴴ` as output.


See also [`left_null(!)`](@ref left_null), [`left_orth(!)`](@ref left_orth), [`right_orth(!)`](@ref right_orth)
