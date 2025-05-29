```
bounds(xs, [dims::Tuple]) => Tuple{Vararg{Tuple{T,T}}}
bounds(xs::Tuple) => Tuple{Vararg{Tuple{T,T}}}
bounds(x, dim) => Tuple{T,T}
bounds(dim::Union{Dimension,Lookup}) => Tuple{T,T}
```

Return the bounds of all dimensions of an object, of a specific dimension, or of a tuple of dimensions.

If bounds are not known, one or both values may be `nothing`.

`dims` can be a `Dimension`, a dimension type, or a tuple of either.
