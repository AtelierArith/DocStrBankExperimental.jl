```
cholinv(input)
```

Calculate the inverse of the input matrix `input` using Cholesky factorization. This function is an alias for `inv(fastcholesky(input))`.

```jldoctest; setup = :(using FastCholesky, LinearAlgebra)
julia> A = [4.0 2.0; 2.0 5.0];

julia> A_inv = cholinv(A);

julia> A_inv ≈ inv(A)
true
```
