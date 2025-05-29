```
datasummary(n::AbstractMillNode)
```

ノード `n` のパラメータの概要を表示します。

# 例

```jldoctest
julia> n = ProductNode(ArrayNode(randn(2, 3)))
ProductNode  3 obs
  ╰── ArrayNode(2×3 Array with Float64 elements)  3 obs

julia> datasummary(n)
"Data summary: 3 obs, 104 bytes."
```

関連情報: [`modelsummary`](@ref).
