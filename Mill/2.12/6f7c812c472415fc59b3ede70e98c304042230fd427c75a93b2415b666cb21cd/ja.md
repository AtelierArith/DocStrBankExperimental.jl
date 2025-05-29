```
ArrayNode(d::AbstractArray, m=nothing)
```

データ `d` とメタデータ `m` を持つ新しい [`ArrayNode`](@ref) を構築します。

# 例

```jldoctest
julia> a = ArrayNode([1 2; 3 4; 5 6])
3×2 ArrayNode{Matrix{Int64}, Nothing}:
 1  2
 3  4
 5  6
```

参照: [`AbstractMillNode`](@ref), [`ArrayModel`](@ref).
