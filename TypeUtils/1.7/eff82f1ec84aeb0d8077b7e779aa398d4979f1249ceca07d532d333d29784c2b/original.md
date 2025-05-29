```
as_array_shape(args...) -> r::Union{Dims,ArraysAxes}
```

converts array dimensions or ranges `args...` to a canonical form of array shape, one of:

  * array size, that is a tuple of `Int`s. This is the result if all of `args...` are integers or instances of `Base.OneTo`, the latter, if any, being replaced by their lengths.
  * array axes, that is a tuple of `AbstractUnitRange{Int}`s. This is the result if any of `args...` are non-`Base.OneTo` ranges, the integers being converted to instances of `Base.OneTo{eltype(Dims)}`.

The array dimensions or ranges may also be provided as a tuple. [`RelaxedArrayShape{N}`](@ref) is the union of types of `N`-tuples to which `as_array_shape` is applicable.

Also see [`as_array_size`](@ref), [`as_array_axes`](@ref), [`ArrayAxes`](@ref), `Dims`, and [`new_array`](@ref).
