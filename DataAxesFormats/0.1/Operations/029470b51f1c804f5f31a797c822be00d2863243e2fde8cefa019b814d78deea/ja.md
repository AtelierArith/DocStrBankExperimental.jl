```
sum_dtype_for(
    element_type::Type{<:StorageReal},
    dtype::Maybe{Type{<:StorageReal}}
)::Type{<:StorageReal}
```

入力 `element_type` に対して、多くのそのような値を合計する操作の結果に使用するデータ型を返します（例： [`Sum`](@ref)）。もし `dtype` が `nothing` でなければ、それが代わりに返されます。

これにより、浮動小数点型と64ビット型はそのまま保持されますが、任意の小さな整数型は対応する32ビット型に昇格されます（例：入力型が `UInt8` の場合、合計型は `UInt32` になります）。
