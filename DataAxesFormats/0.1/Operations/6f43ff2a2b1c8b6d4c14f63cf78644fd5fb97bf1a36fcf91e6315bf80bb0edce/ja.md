```
unsigned_dtype_for(
    element_type::Type{<:StorageReal},
    dtype::Maybe{Type{<:StorageReal}}
)::Type
```

入力 `element_type` に基づいて、値の符号を破棄する操作の結果に使用するデータ型を返します（例：[`Abs`](@ref)）。もし `dtype` が `nothing` でない場合、それが代わりに返されます。
