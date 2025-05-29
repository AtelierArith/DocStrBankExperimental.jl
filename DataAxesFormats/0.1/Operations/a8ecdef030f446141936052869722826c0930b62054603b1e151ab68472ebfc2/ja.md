```
float_dtype_for(
    element_type::Type{<:StorageReal},
    dtype::Maybe{Type{<:StorageReal}}
)::Type{<:AbstractFloat}
```

入力 `element_type` に基づいて、常に浮動小数点値を生成する操作の結果に使用するデータ型を返します（例： [`Log`](@ref)）。もし `dtype` が `nothing` でない場合、それが代わりに返されます。
