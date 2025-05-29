```
getproperties(object, names::Tuple{Vararg{Symbol}})
```

Extract a set of properties with the given `names` from an `object`, returning a new object with just those properties.

# Example

Extract properties `a` and `c` from a `NamedTuple`.

```julia
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> getproperties(nt, (:a, :c))
(a = 1, c = false)
```
