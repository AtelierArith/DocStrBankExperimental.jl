```
ArraySize
```

is the union of types eligible to define array size. Calling `as_array_size(dims)` on any argument `dims` such that `isa(dims,ArraySize)` is true yields an array size in canonical form, that is an instance of `Dims{N}` which is an alias for an `N`-tuple of `Int`.
