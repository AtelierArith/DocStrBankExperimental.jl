```
reversecholesky!(A::AbstractMatrix, NoPivot(); check = true) -> ReverseCholesky
```

The same as [`reversecholesky`](@ref), but saves space by overwriting the input `A`, instead of creating a copy. An [`InexactError`](@ref) exception is thrown if the factorization produces a number not representable by the element type of `A`, e.g. for integer types. ```
