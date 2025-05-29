```
setebc!(
    self::F,
    fenids::AbstractVector{IT},
    is_fixed::Bool,
    comp::IT,
    val::T = 0.0,
) where {T<:Number, IT<:Integer}
```

EBC（本質境界条件）を設定します。

`fenids`         - Nノード識別子の配列 `is_fixed` = スカラーBoolean: 自由度が固定されているか（true）または解放されているか（false）、`comp` = 整数、どの自由度（成分）、`val` = 型Tのスカラー

注意: `setebc!()`への任意の呼び出しは、自由度が自由であるものと固定されているものの現在の割り当てを潜在的に変更するため、現在の自由度番号付けを無効にすることが推定されます。
