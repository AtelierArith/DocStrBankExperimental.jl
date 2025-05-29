```
left_orth(A; [kind::Symbol, trunc, alg_qr, alg_polar, alg_svd]) -> V, C
left_orth!(A, [VC]; [kind::Symbol, trunc, alg_qr, alg_polar, alg_svd]) -> V, C
```

Compute an orthonormal basis `V` for the image of the matrix `A` of size `(m, n)`, as well as a  matrix `C` (the corestriction) such that `A` factors as `A = V * C`. The keyword argument `kind` can be used to specify the specific orthogonal decomposition that should be used to factor `A`, whereas `trunc` can be used to control the precision in determining the rank of `A` via its singular values.

`trunc` can either be a truncation strategy object or a NamedTuple with fields `atol`, `rtol`, and `maxrank`.

This is a high-level wrapper and will use one of the decompositions [`qr_compact!`](@ref), [`svd_compact!`](@ref)/[`svd_trunc!`](@ref), and[`left_polar!`](@ref) to compute the orthogonal basis `V`, as controlled by the keyword arguments.

When `kind` is provided, its possible values are

  * `kind == :qr`: `V` and `C` are computed using the QR decomposition.   This requires `isnothing(trunc)` and `left_orth!(A, [VC])` is equivalent to   `qr_compact!(A, [VC], alg)` with a default value `alg = select_algorithm(qr_compact!, A; positive=true)`
  * `kind == :polar`: `V` and `C` are computed using the polar decomposition,   This requires `isnothing(trunc)` and `left_orth!(A, [VC])` is equivalent to   `left_polar!(A, [VC], alg)` with a default value `alg = select_algorithm(left_polar!, A)`
  * `kind == :svd`: `V` and `C` are computed using the singular value decomposition `svd_trunc!` when a   truncation strategy is specified using the `trunc` keyword argument, and using `svd_compact!` otherwise.   `V` will contain the left singular vectors and `C` is computed as the product of the singular   values and the right singular vectors, i.e. with `U, S, Vᴴ = svd(A)`, we have   `V = U` and `C = S * Vᴴ`.

When `kind` is not provided, the default value is `:qr` when `isnothing(trunc)` and `:svd` otherwise. Finally, finer control is obtained by providing an explicit algorithm for backend factorizations through the `alg_qr`, `alg_polar`, and `alg_svd` keyword arguments, which will only be used if the corresponding factorization is called based on the other inputs. If NamedTuples are passed as `alg_qr`, `alg_polar`, or `alg_svd`, a default algorithm is chosen with `select_algorithm` and the NamedTuple is passed as keyword arguments to that algorithm. `alg_qr` defaults to `(; positive=true)` so that by default a positive QR decomposition will be used.

!!! note
    The bang method `left_orth!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `CV` as output.


See also [`right_orth(!)`](@ref right_orth), [`left_null(!)`](@ref left_null), [`right_null(!)`](@ref right_null)
