```
as_eltype(T, A) -> B
```

yields an array which lazily converts its entries to type `T`. More specifically, a call like `B[i]` yields `as(T,A[i])`.

Consider using [`convert_eltype(T, A)`](@ref convert_eltype) to perform the conversion once and immediately.
