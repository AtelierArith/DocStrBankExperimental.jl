```
cholinv_logdet(input)
```

Calculate the inverse and the natural logarithm of the determinant of the input matrix `input` simultaneously using Cholesky factorization.

```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> A = [4.0 2.0; 2.0 5.0];

julia> A_inv, logdet_A = cholinv_logdet(A);

julia> isapprox(A_inv * A, I)
true

julia> isapprox(logdet_A, log(det(A)))
true
```
