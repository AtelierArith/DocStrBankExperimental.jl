```
setebc!(
    self::F,
    fenid::IT1,
    is_fixed::Bool,
    comp::IT2,
    val::T,
) where {F<:AbstractField,T<:Number,IT1<:Integer,IT2<:Integer}
```

EBC（本質境界条件）を設定します。

`fenids`         - Nノード識別子の配列 `is_fixed` = スカラーBoolean: 自由度が固定されているか（true）または解放されているか（false）、`comp` = 整数、どの自由度（成分）、`val` = 型TのN値の配列

注意: `setebc!()`への任意の呼び出しは、自由度が自由であるものと固定されているものの現在の割り当てを変更する可能性があり、したがって現在の自由度番号付けを無効にすることが推定されます。
