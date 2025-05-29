```
RelaxedArrayShape{N}
```

is like [`ArrayShape{N}`](@ref) but also includes `AbstractRange{<:Integer}}}`s (not just `AbstractUnitRange{<:Integer}`s).

Methods [`as_array_shape`](@ref), [`as_array_axes`](@ref), and [`as_array_size`](@ref) may be called on any argument of type `RelaxedArrayShape{N}` to convert it to a canonical form of array axes or size. Likewise, methods [`as_array_dim`](@ref) and [`as_array_axis`](@ref) may be called on any argument of type `eltype(RelaxedArrayShape)` to convert it to a canonical array dimension length or axis. All these methods assert that all ranges have a unit step.

!!! warning
    It is preferable to use [`ArrayShape{N}`](@ref) which better reflects Julia style.

