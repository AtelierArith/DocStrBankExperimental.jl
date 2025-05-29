```
BagNode(d, b, m=nothing)
```

データ `d`、バッグ `b`、およびメタデータ `m` を持つ新しい [`BagNode`](@ref) を構築します。

`d` は [`AbstractMillNode`](@ref) または `missing` である必要があります。他のタイプは [`ArrayNode`](@ref) にラップされます。

`b` が `AbstractVector` の場合、最初に [`Mill.bags`](@ref) が適用されます。

# 例

```jldoctest
julia> BagNode(ArrayNode(maybehotbatch([1, missing, 2], 1:2)), AlignedBags([1:1, 2:3]))
BagNode  2 obs
  ╰── ArrayNode(2×3 MaybeHotMatrix with Union{Missing, Bool} elements)  3 obs

julia> BagNode(randn(2, 5), [1, 2, 2, 1, 1])
BagNode  2 obs
  ╰── ArrayNode(2×5 Array with Float64 elements)  5 obs
```

参照: [`WeightedBagNode`](@ref)、[`AbstractBagNode`](@ref)、     [`AbstractMillNode`](@ref)、[`BagModel`](@ref)。
