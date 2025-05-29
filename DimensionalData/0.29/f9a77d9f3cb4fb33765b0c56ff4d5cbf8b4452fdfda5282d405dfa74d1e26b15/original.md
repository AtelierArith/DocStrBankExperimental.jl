```
lookup(x::Dimension) => Lookup
lookup(x, [dims::Tuple]) => Tuple{Vararg{Lookup}}
lookup(x::Tuple) => Tuple{Vararg{Lookup}}
lookup(x, dim) => Lookup
```

Returns the [`Lookup`](@ref) of a dimension. This dictates properties of the dimension such as array axis and lookup order, and sampling properties.

`dims` can be a `Dimension`, a dimension type, or a tuple of either.

This is separate from `val` in that it will only work when dimensions actually contain an `AbstractArray` lookup, and can be used on a  `DimArray` or `DimStack` to retrieve all lookups, as there is no ambiguity  of meaning as there is with `val`.
