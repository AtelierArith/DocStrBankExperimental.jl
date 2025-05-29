```
deleteproperties(object, names::Tuple{Vararg{Symbol}})
```

Return a copy of `object` with the property with the given `names` removed.

# Example

```
julia> nt = (a = 1, b = 2.0, c = false, d = "abc")
(a = 1, b = 2.0, c = false)

julia> deleteproperties(nt, (:b, :d))
(a = 1, c = false)
```
