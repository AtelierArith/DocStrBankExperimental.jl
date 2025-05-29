```
outcometype(::Type{<:AbstractModel{O}}) where {O} = O
outcometype(m::AbstractModel) = outcometype(typeof(m))
```

モデル（タイプ）の結果タイプを返します。

詳細は [`AbstractModel`](@ref) を参照してください。
