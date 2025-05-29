```
coefftype(::Type{L}) where L <: AbstractLinear{T,R} = R
coefftype(a::L) where L <: AbstractLinear{T,R} = R
```

線形結合における係数の型を返します。

関連情報として [`termtype`](@ref) を参照してください。
