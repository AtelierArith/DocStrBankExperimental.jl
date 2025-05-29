```
setebc!(
    self::F,
    fenids::AbstractVector{IT},
    is_fixed::Bool,
    comp::AbstractVector{IT},
    val::T = 0.0,
) where {T<:Number, IT<:Integer}
```

EBC（本質境界条件）を設定します。

`fenids` = Nノード識別子の配列 `comp` = 自由度（成分）の整数ベクトル、 `val` = 型 `T` のスカラー、デフォルトは `0.0`

注意: `setebc!()` への任意の呼び出しは、自由度が自由であるものと固定されているものの現在の割り当てを変更する可能性があり、したがって現在の自由度番号付けを無効にすることが推定されます。
