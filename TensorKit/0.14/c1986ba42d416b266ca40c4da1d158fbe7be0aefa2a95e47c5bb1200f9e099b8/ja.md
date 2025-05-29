```
numin(::Union{TT,Type{TT}}) where {TT<:AbstractTensorMap} -> Int
```

テンソルの入力空間の数を返します。これは、そのテンソルの定義域における空間の数と同等です。

関連情報として、[`numout`](@ref) および [`numind`](@ref) を参照してください。
