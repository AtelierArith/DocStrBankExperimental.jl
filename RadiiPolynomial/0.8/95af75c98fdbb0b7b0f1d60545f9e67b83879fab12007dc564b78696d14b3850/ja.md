```
opnorm(A::LinearOperator, X::BanachSpace, Y::BanachSpace)
```

`A`の演算子ノルムを計算します。ここで、`X`は`domain(A)`に対応するバナッハ空間であり、`Y`は`codomain(A)`に対応するバナッハ空間です。

関連情報: [`opnorm(::LinearOperator, ::Real=Inf)`](@ref)、[`opnorm(::LinearOperator, ::BanachSpace)`](@ref) および [`opnorm(::LinearOperator{<:VectorSpace,ParameterSpace}, ::BanachSpace)`](@ref)。
