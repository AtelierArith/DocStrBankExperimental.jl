```
is_fast_array(A)
```

yields whether array `A` has standard 1-based indices and is efficiently indexed by linear indices.

Several arguments can be checked in a single call:

```
is_fast_array(A, B, C, ...)
```

is the same as:

```
is_fast_array(A) && is_fast_array(B) && is_fast_array(C) && ...
```

See also [`IndexingType`](@ref), [`to_fast_array`](@ref), [`is_flat_array`](@ref).
