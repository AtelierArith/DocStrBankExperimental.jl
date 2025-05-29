```
StorageType(A)
```

yields the type of storage of the elements of argument `A`. If `A` is a *flat* array, that is an array with contiguous elements in column-major order and first element at index 1, the singleton `FlatStorage()` is returned; otherwise, the singleton `AnyStorage()` is returned.

This method can be extended for custom array types to quickly return the correct answer.

See also [`is_flat_array`](@ref), [`to_flat_array`](@ref).
