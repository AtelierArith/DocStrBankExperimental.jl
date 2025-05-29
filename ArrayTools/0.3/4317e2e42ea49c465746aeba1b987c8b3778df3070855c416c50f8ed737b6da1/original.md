```
bcastlazy(A, [T=eltype(A),] dims...)
```

yields a *flat* array of type `T` and dimensions `dims` whose values are given by `A` according to type conversion and broadcasting rules (see `broadcast` method). Compared to [`bcastcopy`](@ref), making a copy of `A` is avoided if it is already an array with the correct type of elements and dimensions or if it can be reshaped (by the `reshape` method) to the correct type and dimensions. This means that the result may share the same contents as `A`. Argument `A` can be a scalar or an array with 1-based indices. The result has 1-based indices and contiguous elements which is suitable for fast linear indexing.

See also [`bcastcopy`](@ref), [`bcastsize`](@ref).
