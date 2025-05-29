```
numind(::Union{T,Type{T}}) where {T<:AbstractTensorMap} -> Int
```

テンソルの入力および出力空間の合計数を返します。これは、そのテンソルの定義域と値域の空間の合計数に相当します。

また、[`numout`](@ref)および[`numin`](@ref)も参照してください。
