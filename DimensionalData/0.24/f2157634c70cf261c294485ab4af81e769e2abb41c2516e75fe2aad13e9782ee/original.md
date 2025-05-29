```
lookup(x::Dimension) => LookupArray
lookup(x, [dims::Tuple]) => Tuple{Vararg{LookupArray}}
lookup(x::Tuple) => Tuple{Vararg{LookupArray}}
lookup(x, dim) => LookupArray
```

Returns the [`LookupArray`](@ref) of a dimension. This dictates properties of the dimension such as array axis and index order, and sampling properties.

`dims` can be a `Dimension`, a dimension type, or a tuple of either.
