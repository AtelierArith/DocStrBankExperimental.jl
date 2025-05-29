```
as_array_size(args...) -> dims::Dims
```

converts array dimensions or ranges `args...` to a canonical form of array size, that is a tuple of `eltype(Dims)`s. Any range in `args...` is replaced by its length.

The array dimensions or ranges may also be provided as a tuple. [`RelaxedArrayShape{N}`](@ref) is the union of types of `N`-tuples to which `as_array_size` is applicable.

Also see [`as_array_shape`](@ref), [`as_array_axes`](@ref), [`as_array_dim`](@ref), `Dims`, and [`new_array`](@ref).
