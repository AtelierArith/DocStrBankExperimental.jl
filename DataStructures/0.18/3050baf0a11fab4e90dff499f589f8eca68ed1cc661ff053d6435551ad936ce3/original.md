```
haskey(collection, key) -> Bool
```

Determine whether a collection has a mapping for a given `key`.

# Examples

```jldoctest
julia> D = SwissDict('a'=>2, 'b'=>3)
SwissDict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> haskey(D, 'a')
true

julia> haskey(D, 'c')
false
```
