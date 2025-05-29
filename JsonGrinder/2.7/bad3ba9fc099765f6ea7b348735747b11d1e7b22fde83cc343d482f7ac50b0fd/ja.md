```
PolymorphExtractor
```

異なるエクストラクタの結果である各アイテムを持つ `Mill.ProductNode` に抽出します。

# 例

```jldoctest
julia> e = (NGramExtractor(), CategoricalExtractor(["tcp", "udp", "dhcp"])) |> PolymorphExtractor
PolymorphExtractor
  ├── NGramExtractor(n=3, b=256, m=2053)
  ╰── CategoricalExtractor(n=4)

julia> e("tcp")
ProductNode  1 obs
  ├── ArrayNode(2053×1 NGramMatrix with Int64 elements)  1 obs
  ╰── ArrayNode(4×1 OneHotArray with Bool elements)  1 obs

julia> e("http")
ProductNode  1 obs
  ├── ArrayNode(2053×1 NGramMatrix with Int64 elements)  1 obs
  ╰── ArrayNode(4×1 OneHotArray with Bool elements)  1 obs
```
