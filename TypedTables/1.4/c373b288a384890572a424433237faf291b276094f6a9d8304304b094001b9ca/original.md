```
deleteproperty(object, name::Symbol)
```

Return a copy of `object` with the property with the given `name` removed.

# Example

```
julia> nt = (a = 1, b = 2.0, c = false)
(a = 1, b = 2.0, c = false)

julia> deleteproperty(nt, :b)
(a = 1, c = false)
```
