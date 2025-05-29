```
eigenvalues_simple(A::AcbMatrix, algorithm::Symbol = :default)
```

Returns the eigenvalues of `A` as a vector of `AcbFieldElem`. It is assumed that `A` has only simple eigenvalues.

The algorithm used can be changed by setting the `algorithm` keyword to `:vdhoeven_mourrain` or `:rump`.

This function is experimental.
