```
UncertainValue(t::Distributions.Truncated)
```

分布のインスタンスから不確実な値を構築します。特定の不確実な値タイプが実装されていない場合、パラメータの数は分布から決定され、次のいずれかのタイプのインスタンスが返されます：

  * `ConstrainedUncertainScalarValueOneParameter`
  * `ConstrainedUncertainScalarValueTwoParameter`
  * `ConstrainedUncertainScalarValueThreeParameter`

## 例

```julia
# 区間 [0.5, 0.7] に切り取られた正規分布
t = truncated(Normal(0, 1), 0.5, 0.7)
UncertainValue(t)

# 区間 [0.5, 3.5] に切り取られたガンマ分布
t = Truncate(Gamma(4, 5.1), 0.5, 3.5)
UncertainValue(t)

# 区間 [2, 7] に切り取られた二項分布
t = Truncate(Binomial(10, 0.4), 2, 7)
UncertainValue(t)
```
