```
ArrayExtractor{T}
```

Extracts all items in an `Array` and returns them as a `Mill.BagNode`.

# Examples

```jldoctest
julia> e = ArrayExtractor(CategoricalExtractor(2:4))
ArrayExtractor
  ╰── CategoricalExtractor(n=4)

julia> e([2, 3, 1, 4])
BagNode  1 obs
  ╰── ArrayNode(4×4 OneHotArray with Bool elements)  4 obs
```
