```
mergenodes(
    fens::FENodeSet{T},
    fes::AbstractFESet,
    tolerance::T,
    candidates::AbstractVector{IT},
) where {T<:Number, IT<:Integer}
```

単一のノードセットのノードを統合します。

`mergenodes(fens, fes, tolerance)`と似ていますが、マージの対象となるのは候補ノードのみです。これにより、操作の速度が桁違いに向上する可能性があります。
