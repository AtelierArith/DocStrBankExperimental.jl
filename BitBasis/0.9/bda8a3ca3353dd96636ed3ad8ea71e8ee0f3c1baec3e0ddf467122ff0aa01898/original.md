```
anyone(index::Integer, mask::Integer) -> Bool
```

Return `true` if any masked position of index is 1.

# Example

`true` if any masked positions is 1.

```jldoctest
julia> anyone(0b1011, 0b1001)
true

julia> anyone(0b1011, 0b1100)
true

julia> anyone(0b1011, 0b0100)
false
```
