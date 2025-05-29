```
Mill.data(n::AbstractMillNode)
```

ノード `n` に格納されているデータを返します。

# 例

```jldoctest
julia> Mill.data(ArrayNode([1 2; 3 4], "metadata"))
2×2 Matrix{Int64}:
 1  2
 3  4

julia> Mill.data(BagNode(ArrayNode([1 2; 3 4]), [1, 2], "metadata"))
2×2 ArrayNode{Matrix{Int64}, Nothing}:
 1  2
 3  4
```

参照: [`Mill.metadata`](@ref)
