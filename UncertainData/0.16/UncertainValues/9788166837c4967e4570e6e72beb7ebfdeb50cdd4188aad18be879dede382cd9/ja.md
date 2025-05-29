```
UncertainValue(d::Distributions.Distribution)
```

分布のインスタンスから不確実な値を構築します。特定の不確実な値の型が実装されていない場合、パラメータの数は分布から決定され、次のいずれかの型のインスタンスが返されます：

  * `UncertainScalarTheoreticalOneParameter`
  * `UncertainScalarTheoreticalTwoParameter`
  * `UncertainScalarTheoreticalThreeParameter`

## 例

```julia
UncertainValue(Normal(0, 1))
UncertainValue(Gamma(4, 5.1))
UncertainValue(Binomial, 8, 0.2)
```
