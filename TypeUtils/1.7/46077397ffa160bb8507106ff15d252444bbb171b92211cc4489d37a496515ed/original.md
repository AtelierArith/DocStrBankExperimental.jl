```
as_array_dim(arg) -> dim::eltype(Dims)
```

converts array dimension or range `arg` to a canonical array dimension, that is an `eltype(Dims)`. If `arg` is a unit-step range, its length is returned. [`eltype(RelaxedArrayShape)`](@ref RelaxedArrayShape) is the union of types to which `as_array_dim` is applicable.

Also see [`as_array_size`](@ref), [`as_array_axis`](@ref), and `Dims`.
