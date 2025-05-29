```
positive_definite(X::AbstractMatrix{<:Real}, ε = eps(T))
```

Produce a parameter whose `value` is constrained to be a strictly positive-definite matrix. The argument `X` minus `ε` times the identity needs to be a positive-definite matrix (see https://en.wikipedia.org/wiki/Definite_matrix). The optional second argument `ε` must be a positive real number.

The unconstrained parameter is a `LowerTriangular` matrix, stored as a vector.
