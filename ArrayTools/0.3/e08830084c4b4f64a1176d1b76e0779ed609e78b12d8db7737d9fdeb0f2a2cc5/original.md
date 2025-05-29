```
IndexingType(A)
```

yields one of the singletons `FastIndexing()` or `AnyIndexing()` to indicate whether or not array `A` has standard 1-based indices and can be efficiently indexed by one integer (even if `A` is multidimensional) and column-major ordering is used to access the elements of `A`.

This method can be extended for custom array types to quickly return the correct answer.

See also [`is_fast_array`](@ref), [`to_fast_array`](@ref).
