```
identityoperator(a::Basis[, b::Basis])
identityoperator(::Type{<:AbstractOperator}, a::Basis[, b::Basis])
identityoperator(::Type{<:Number}, a::Basis[, b::Basis])
identityoperator(::Type{<:AbstractOperator}, ::Type{<:Number}, a::Basis[, b::Basis])
```

与えられた基底でアイデンティティ演算子を返します。オプションで、[`AbstractOperator`](@ref) のサブタイプであるコンテナタイプと、アイデンティティ行列で使用する数値タイプを指定できます。
