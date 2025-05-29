```
length2bags(ls::Vector{<:Integer})
```

`ls`で与えられた袋の長さを、連続したブロックを持つ[`AlignedBags`](@ref)に変換します。

# 例

```jldoctest
julia> length2bags([1, 3, 2])
AlignedBags{Int64}(UnitRange{Int64}[1:1, 2:4, 5:6])
```

関連情報: [`AlignedBags`](@ref).
