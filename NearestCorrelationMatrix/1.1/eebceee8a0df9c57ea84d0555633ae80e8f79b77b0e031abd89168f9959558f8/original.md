```
init(prob, alg, args...; kwargs...)
```

Initialize the solver with the given algorithm.

## Keyword Arguments

  * `alias_A`: Whether to alias the matrix $A$ or use a copy by default. When `true`, algorithms that operate in place can save memory by reusing $A$. Defaults to `true` if the algorithm is known not to modify $A$, and `false` otherwise.
  * `abstol`: The absolute tolerance. Defaults to `√(eps(eltype(A)))`.
  * `reltol`: The relative tolerance. Defaults to `√(eps(eltype(A)))`.
  * `maxiters`: The number of iterations allowed. Defaults to `size(A,1)`
  * `fix_sym`: If `true`, then makes the input matrix symmetric if it is not already. Defaults  to `false`, and init will fail if the input matrix is not symmetric.
  * `uplo`: If `fix_sym` is `true`, then the upper (`:U`) or lower (`:L`) triangle of the input is used to make a symmetric matrix. Defaults to `:U`.
  * `convert_f16`: If the algorithm does not support `Float16` values, then the input matrix will be converted to an `AbstractMatrix{Float32}`. Defaults to `false`, and init will fail if the algorithm does not support `Float16`.
  * `force_f16`: If `true`, then the algorithm will be forced to use the input matrix, even if the algorithm doesn't fully support `Float16` values in a stable way.
  * `ensure_pd`: Checks (and corrects) that the resulting matrix is positive definite. Defaults to `false`.
  * `verbose`: Whether to print extra information. Defaults to `false`.
