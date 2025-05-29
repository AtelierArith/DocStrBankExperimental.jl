```
opnorm(A::LinearOperator{<:VectorSpace,ParameterSpace}, X::BanachSpace)
```

`A`の演算子ノルムを計算します。ここで、`X`は`domain(A)`に対応するバナッハ空間です。

関連情報: [`opnorm(::LinearOperator, ::Real=Inf)`](@ref)、[`opnorm(::LinearOperator, ::BanachSpace, ::BanachSpace)`](@ref) および [`opnorm(::LinearOperator, ::BanachSpace)`](@ref)。
