```
replacein(n, old, new)
```

データノードまたはモデル `n` の中で、`old` の各出現を `new` に置き換えます。

短い説明

# 例

```jldoctest
julia> n = ProductNode((BagNode(randn(2, 2), bags([0:-1, 0:-1])), ArrayNode([1 2; 3 4])))
ProductNode  2 obs
  ├── BagNode  2 obs
  │     ╰── ArrayNode(2×2 Array with Float64 elements)  2 obs
  ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs

julia> replacein(n, n.data[1], ArrayNode(maybehotbatch([1, 2], 1:2)))
ProductNode  2 obs
  ├── ArrayNode(2×2 MaybeHotMatrix with Bool elements)  2 obs
  ╰── ArrayNode(2×2 Array with Int64 elements)  2 obs
```
