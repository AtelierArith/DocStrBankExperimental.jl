```
opnorm(A::LinearOperator, X::BanachSpace)
```

`A`の演算子ノルムを計算します。ここで、`X`は`domain(A)`と`codomain(A)`の両方に対応するバナッハ空間です。

関連情報: [`opnorm(::LinearOperator, ::Real=Inf)`](@ref), [`opnorm(::LinearOperator, ::BanachSpace, ::BanachSpace)`](@ref) および [`opnorm(::LinearOperator{<:VectorSpace,ParameterSpace}, ::BanachSpace)`](@ref).
