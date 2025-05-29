```
Solver(D1, D2 = nothing, D3 = nothing)
```

ソルバーを作成します。ここで、`D1`は[SummationByPartsOperators.jl](https://github.com/ranocha/SummationByPartsOperators.jl)の`derivative_order`が1の`AbstractDerivativeOperator`、`D2`は`derivative_order`が2の`AbstractDerivativeOperator`または`AbstractMatrix`、`D3`は`derivative_order`が3の`AbstractDerivativeOperator`または`AbstractMatrix`です。`D2`と`D3`は、離散化でその導関数が使用されない場合は`nothing`にすることもできます。与えられたすべての部分和演算子は、同じグリッドに関連付けられている必要があります。
