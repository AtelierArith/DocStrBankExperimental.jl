```
issuccess(F::Factorization)
```

Test that a factorization of a matrix succeeded.

!!! compat "Julia 1.6"
    `issuccess(::CholeskyPivoted)` requires Julia 1.6 or later.


```jldoctest
julia> F = cholesky([1 0; 0 1]);

julia> issuccess(F)
true

julia> F = lu([1 0; 0 0]; check = false);

julia> issuccess(F)
false
```
