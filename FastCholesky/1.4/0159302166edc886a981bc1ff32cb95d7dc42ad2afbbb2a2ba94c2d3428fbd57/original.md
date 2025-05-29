```
fastcholesky!(input; fallback_gmw81=true, symmetrize_input=true, gmw81_tol=PositiveFactorizations.default_δ(input), symmetric_tol=1e-8)
```

Calculate the Cholesky factorization of the input matrix `input` in-place. This function is an in-place version of `fastcholesky`. It first checks if the input matrix is symmetric, and if it is, it will use the built-in Cholesky factorization by wrapping the input in a `Hermitian` matrix. If the input matrix is not symmetric and `symmetrize_input=true`, it will symmetrize the input matrix and try again recursively. If the input matrix is not symmetrics, not positive definite, and `fallback_gmw81=true`, it will use the `GMW81` algorithm as a fallback. In other cases, it will throw an error.

# Keyword arguments

  * `fallback_gmw81::Bool=true`: If true, the function will use the `GMW81` algorithm as a fallback if the input matrix is not positive definite.
  * `symmetrize_input::Bool=true`: If true, the function will symmetrize the input matrix before retrying the Cholesky factorization in case if the first attempt failed.
  * `gmw81_tol::Real=PositiveFactorizations.default_δ(input)`: The tolerance for the positive-definiteness of the input matrix for the `GMW81` algorithm.
  * `symmetric_tol::Real=1e-8`: The tolerance for the symmetry of the input matrix.

!!! note
    Use this function only when you expect the input matrix to be nearly positive definite.


```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> C = fastcholesky!([ 1.0 0.5; 0.5 1.0 ]);

julia> C.L * C.L' ≈ [ 1.0 0.5; 0.5 1.0 ]
true
```
