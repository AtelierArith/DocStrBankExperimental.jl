```
Extent

Extent(; kw...)
Extent(bounds::NamedTuple)
```

A wrapper for a `NamedTuple` of tuples holding the lower and upper bounds for each dimension of the object.

`keys(extent)` will return the dimension name Symbols, in the order the dimensions are used in the object.

`values(extent)` will return a tuple of tuples: `(lowerbound, upperbound)` for each dimension.

# Examples

```julia-repl
julia> ext = Extent(X = (1.0, 2.0), Y = (3.0, 4.0))
Extent(X = (1.0, 2.0), Y = (3.0, 4.0))

julia> keys(ext)
(:X, :Y)

julia> values(ext)
((1.0, 2.0), (3.0, 4.0))
```
