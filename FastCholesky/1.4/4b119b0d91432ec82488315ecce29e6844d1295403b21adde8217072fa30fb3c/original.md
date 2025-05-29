```
cholsqrt(input)
```

Calculate the Cholesky square root of the input matrix `input`. This function is an alias for `fastcholesky(input).L`. NOTE: This is not equal to the standard matrix square root used in literature, which requires the result to be symmetric.

```jldoctest
julia> A = [4.0 2.0; 2.0 5.0];

julia> A_sqrt = cholsqrt(A);

julia> isapprox(A_sqrt * A_sqrt', A)
true
```
