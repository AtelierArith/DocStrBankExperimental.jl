```
allone(index::Integer, mask::Integer) -> Bool
```

Return `true` if all masked position of index is 1.

# Example

`true` if all masked positions are 1.

```jldoctest
julia> allone(0b1011, 0b1011)
true

julia> allone(0b1011, 0b1001)
true

julia> allone(0b1011, 0b0100)
false
```
