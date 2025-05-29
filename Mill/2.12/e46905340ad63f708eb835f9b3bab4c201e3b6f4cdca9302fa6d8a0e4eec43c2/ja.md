```
mapdata(f, x)
```

再帰的に `f` を `x` のすべての葉のデータに適用します。

# 例

```jldoctest
julia> n1 = ProductNode(a=zeros(2,2), b=ones(2,2))
ProductNode  2 obs
  ├── a: ArrayNode(2×2 Array with Float64 elements)  2 obs
  ╰── b: ArrayNode(2×2 Array with Float64 elements)  2 obs

julia> n2 = Mill.mapdata(x -> x .+ 1, n1)
ProductNode  2 obs
  ├── a: ArrayNode(2×2 Array with Float64 elements)  2 obs
  ╰── b: ArrayNode(2×2 Array with Float64 elements)  2 obs

julia> Mill.data(n2).a
2×2 ArrayNode{Matrix{Float64}, Nothing}:
 1.0  1.0
 1.0  1.0

julia> Mill.data(n2).b
2×2 ArrayNode{Matrix{Float64}, Nothing}:
 2.0  2.0
 2.0  2.0
```
