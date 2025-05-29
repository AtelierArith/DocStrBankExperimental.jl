```
setebc!(
    self::F,
    fenids::AbstractVector{IT},
    is_fixed::Bool,
    comp::IT,
    val::AbstractVector{T},
) where {T<:Number, IT<:Integer}
```

EBC（本質境界条件）を設定します。

`fenids`         - N ノード識別子の配列 `is_fixed` = スカラー Boolean: 自由度が固定されているか (true) または解放されているか (false)、`comp` = 整数、どの自由度 (成分) か、`val` = 型 T の N 値の配列

注意: `setebc!()` への任意の呼び出しは、自由度が自由であるか固定されているかの現在の割り当てを変更する可能性があり、したがって現在の自由度番号付けを無効にすることが推定されます。
