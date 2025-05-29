```
as_array_axis(arg) -> rng::ArrayAxis
```

converts array dimension or range `arg` to a canonical array axis, that is an instance of `AbstractUnitRange{eltype(Dims)}`. If `arg` is an integer, `Base.OneTo{eltype(Dims)}(arg)` is returned. [`eltype(RelaxedArrayShape)`](@ref RelaxedArrayShape) is the union of types to which `as_array_axis` is applicable.

Also see [`as_array_axes`](@ref), [`as_array_dim`](@ref), and `Dims`.
