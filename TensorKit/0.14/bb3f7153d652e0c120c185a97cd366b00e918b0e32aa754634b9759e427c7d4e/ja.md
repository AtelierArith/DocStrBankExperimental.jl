```
numout(::Union{TT,Type{TT}}) where {TT<:AbstractTensorMap} -> Int
```

テンソルの出力空間の数を返します。これは、そのテンソルのコドメインにおける空間の数に相当します。

関連情報として、[`numin`](@ref) と [`numind`](@ref) を参照してください。
