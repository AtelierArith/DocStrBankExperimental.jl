```
ArrayExtractor{T}
```

`Array`内のすべてのアイテムを抽出し、それらを`Mill.BagNode`として返します。

# 例

```jldoctest
julia> e = ArrayExtractor(CategoricalExtractor(2:4))
ArrayExtractor
  ╰── CategoricalExtractor(n=4)

julia> e([2, 3, 1, 4])
BagNode  1 obs
  ╰── ArrayNode(4×4 OneHotArray with Bool elements)  4 obs
```
