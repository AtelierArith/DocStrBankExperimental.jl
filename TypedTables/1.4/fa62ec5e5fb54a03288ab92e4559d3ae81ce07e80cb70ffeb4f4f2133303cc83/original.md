```
getproperties(names::Tuple{Vararg{Symbol}})
```

Return a function that extracts a set of properties with the given `names` from an object, returning a new object with just those properties.

Internally, the `names` are stored as a type parameter of a `GetProperties` object for the purpose of constant propagation. You may overload the `propertytype` function to control the type of the object that is returned, which by default will be a `NamedTuple`. See also `getproperty`.

# Example

Extract properties `a` and `c` from a `NamedTuple`.

```julia
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> getproperties((:a, :c))(nt)
(a = 1, c = false)
```
