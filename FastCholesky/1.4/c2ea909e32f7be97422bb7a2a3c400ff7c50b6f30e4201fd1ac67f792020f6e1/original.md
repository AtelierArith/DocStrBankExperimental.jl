```
chollogdet(input)
```

Calculate the log-determinant of the input matrix `input` using Cholesky factorization. This function is an alias for `logdet(fastcholesky(input))`.

```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> A = [4.0 2.0; 2.0 5.0];

julia> logdet_A = chollogdet(A);

julia> isapprox(logdet_A, log(det(A)))
true
```
