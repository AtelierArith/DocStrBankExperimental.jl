```
bcastcopy(A, [T=eltype(A),] dims...)
```

yields a new array of element type `T` and dimensions `dims` whose values are given by `A` according to type conversion and broadcasting rules (like for the `broadcast` method). Compared to [`bcastlazy`](@ref), it is guaranteed that the returned array does not share its contents with `A`.

Argument `A` can be a scalar value or an array.

See also [`bcastlazy`](@ref), [`bcastsize`](@ref).
