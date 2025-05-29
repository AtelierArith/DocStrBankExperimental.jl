```
setindex(collection, v, i::Int)
```

Return a copy of `collection` with the value at index `i` set to `v`.

# Examples

```jldoctest
julia> x = StackVector([true, false])
2-element StackVector{2}:
 1
 0

julia> setindex(x, false, 1)
2-element StackVector{2}:
 0
 0
```
