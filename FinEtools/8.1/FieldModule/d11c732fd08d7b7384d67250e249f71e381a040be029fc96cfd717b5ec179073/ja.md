```
setebc!(
    self::F,
    fenids::AbstractVector{IT},
    comp::IT,
    val::AbstractVector{T},
) where {T<:Number, IT<:Integer}
```

EBC（本質境界条件）を設定します。

`fenids` = N個のノード識別子の配列 `comp` = 自由度（成分）を表す整数、`val` = 型 `T` のN個の値の配列

注意: `setebc!()`への任意の呼び出しは、自由度が自由であるものと固定されているものの現在の割り当てを変更する可能性があり、そのため現在の自由度番号付けが無効になると見なされます。
