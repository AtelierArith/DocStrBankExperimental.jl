```
as_array_axes(args...) -> rngs::ArrayAxes
```

converts array dimensions or ranges `args...` to a canonical form of array axes, that is a tuple of `AbstractUnitRange{eltype(Dims)}`s. Any integer in `args...` is replaced by an instance of `Base.OneTo{eltype(Dims)}`.

The array dimensions or ranges may also be provided as a tuple. [`RelaxedArrayShape{N}`](@ref) is the union of types of `N`-tuples to which `as_array_axes` is applicable.

Also see [`as_array_shape`](@ref), [`as_array_size`](@ref), [`as_array_axis`](@ref), [`ArrayAxes`](@ref), `Dims`, and [`new_array`](@ref).
