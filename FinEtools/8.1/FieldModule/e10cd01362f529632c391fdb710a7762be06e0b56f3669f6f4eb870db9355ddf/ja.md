```
setebc!(
    self::F,
    fenids::AbstractVector{IT},
    comp::IT,
    val::T = 0.0,
) where {T<:Number, IT<:Integer}
```

EBC（本質境界条件）を設定します。

`fenids` = Nノード識別子の配列 `comp` = 自由度（成分）の整数、`val` = 型 `T` のスカラー

注意: `setebc!()` の呼び出しは、自由度が自由であるか固定されているかの現在の割り当てを潜在的に変更するため、現在の自由度番号付けを無効にすることが想定されています。
