```
termtype(::Type{L}) where L <: AbstractLinear{T,R} = T
termtype(a::L) where L <: AbstractLinear{T,R} = T
```

線形結合における項（基底要素）の型を返します。

詳細は [`coefftype`](@ref) を参照してください。
