```
right_orth(A; [kind::Symbol, trunc, alg_lq, alg_polar, alg_svd]) -> C, Vᴴ
right_orth!(A, [CVᴴ]; [kind::Symbol, trunc, alg_lq, alg_polar, alg_svd]) -> C, Vᴴ
```

Compute an orthonormal basis `V = adjoint(Vᴴ)` for the coimage of the matrix `A`, i.e. for the image of `adjoint(A)`, as well as a matrix `C` such that `A = C * Vᴴ`. The keyword argument `kind` can be used to specify the specific orthogonal decomposition that should be used to factor `A`, whereas `trunc` can be used to control the precision in determining the rank of `A` via its singular values.

`trunc` can either be a truncation strategy object or a NamedTuple with fields `atol`, `rtol`, and `maxrank`.

This is a high-level wrapper and will use one of the decompositions [`lq_compact!`](@ref), [`svd_compact!`](@ref)/[`svd_trunc!`](@ref), and [`right_polar!`](@ref) to compute the orthogonal basis `V`, as controlled by the keyword arguments.

When `kind` is provided, its possible values are

  * `kind == :lq`: `C` and `Vᴴ` are computed using the QR decomposition,   This requires `isnothing(trunc)` and `right_orth!(A, [CVᴴ])` is equivalent to   `lq_compact!(A, [CVᴴ], alg)` with a default value `alg = select_algorithm(lq_compact!, A; positive=true)`
  * `kind == :polar`: `C` and `Vᴴ` are computed using the polar decomposition,   This requires `isnothing(trunc)` and `right_orth!(A, [CVᴴ])` is equivalent to   `right_polar!(A, [CVᴴ], alg)` with a default value `alg = select_algorithm(right_polar!, A)`
  * `kind == :svd`: `C` and `Vᴴ` are computed using the singular value decomposition `svd_trunc!` when   a truncation strategy is specified using the `trunc` keyword argument, and using `svd_compact!` otherwise.   `V = adjoint(Vᴴ)` will contain the right singular vectors corresponding to the singular   values and `C` is computed as the product of the singular values and the right singular vectors,   i.e. with `U, S, Vᴴ = svd(A)`, we have `C = rmul!(U, S)` and `Vᴴ = Vᴴ`.

When `kind` is not provided, the default value is `:lq` when `isnothing(trunc)` and `:svd` otherwise. Finally, finer control is obtained by providing an explicit algorithm for backend factorizations through the `alg_lq`, `alg_polar`, and `alg_svd` keyword arguments, which will only be used if the corresponding factorization is called based on the other inputs. If `alg_lq`, `alg_polar`, or `alg_svd` are NamedTuples, a default algorithm is chosen with `select_algorithm` and the NamedTuple is passed as keyword arguments to that algorithm. `alg_lq` defaults to `(; positive=true)` so that by default a positive LQ decomposition will be used.

!!! note
    The bang method `right_orth!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `CVᴴ` as output.


See also [`left_orth(!)`](@ref left_orth), [`left_null(!)`](@ref left_null), [`right_null(!)`](@ref right_null)
