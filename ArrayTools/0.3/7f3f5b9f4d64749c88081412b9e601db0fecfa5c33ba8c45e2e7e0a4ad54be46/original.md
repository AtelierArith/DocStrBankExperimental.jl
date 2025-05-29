```
is_flat_array(A) -> boolean
```

yields whether array `A` can be indexed as a *flat* array, that is an array with contiguous elements in column-major order and first element at index 1. This also means that `A` has 1-based indices along all its dimensions.

Several arguments can be checked in a single call:

```
is_flat_array(A, B, C, ...)
```

is the same as:

```
is_flat_array(A) && is_flat_array(B) && is_flat_array(C) && ...
```

See also [`StorageType`](@ref), [`to_flat_array`](@ref), [`is_fast_array`](@ref), [`has_standard_indexing`](@ref).
