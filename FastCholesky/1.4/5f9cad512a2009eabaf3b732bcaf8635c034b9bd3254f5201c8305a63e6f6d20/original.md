```
fastcholesky(input)
```

Calculate the Cholesky factorization of the input matrix `input`.  This function provides a more efficient implementation for certain input matrices compared to the standard `LinearAlgebra.cholesky` function.  By default, it falls back to using `LinearAlgebra.cholesky(PositiveFactorizations.Positive, input)`, which means it does not require the input matrix to be perfectly symmetric.

!!! note
    This function assumes that the input matrix is nearly positive definite, and it will attempt to make the smallest possible adjustments  to the matrix to ensure it becomes positive definite. Note that the magnitude of these adjustments may not necessarily be small, so it's important to use  this function only when you expect the input matrix to be nearly positive definite.


```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> C = fastcholesky([ 1.0 0.5; 0.5 1.0 ]);

julia> C.L * C.L' ≈ [ 1.0 0.5; 0.5 1.0 ]
true
```
