```
outcometype(::Type{<:AbstractModel{O}}) where {O} = O
outcometype(m::AbstractModel) = outcometype(typeof(m))
```

モデル（型）の結果の型を返します。

詳細は [`AbstractModel`](@ref) を参照してください。
