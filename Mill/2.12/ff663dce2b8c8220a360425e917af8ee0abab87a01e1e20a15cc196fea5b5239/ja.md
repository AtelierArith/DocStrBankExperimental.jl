```
WeightedBagNode(d, b, w::Vector, m=nothing)
```

データ `d`、バッグ `b`、重みのベクトル `w`、およびメタデータ `m` を持つ新しい [`WeightedBagNode`](@ref) を構築します。

`d` は [`AbstractMillNode`](@ref) または `missing` である必要があります。それ以外の型は [`ArrayNode`](@ref) にラップされます。

`b` が `AbstractVector` の場合、最初に [`Mill.bags`](@ref) が適用されます。

# 例

```jldoctest
julia> WeightedBagNode(ArrayNode(NGramMatrix(["s1", "s2"])), bags([1:2, 0:-1]), [0.2, 0.8])
WeightedBagNode  2 obs
  ╰── ArrayNode(2053×2 NGramMatrix with Int64 elements)  2 obs

julia> WeightedBagNode(zeros(2, 2), [1, 2], [1, 2])
WeightedBagNode  2 obs
  ╰── ArrayNode(2×2 Array with Float64 elements)  2 obs
```

関連情報: [`BagNode`](@ref)、[`AbstractBagNode`](@ref)、[`AbstractMillNode`](@ref)、[`BagModel`](@ref)。
