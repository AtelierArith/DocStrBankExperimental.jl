```
ot_plan(c, μ::DiscreteNonParametric, ν::DiscreteNonParametric)
```

一変量離散分布 `μ` と `ν` をソースおよびターゲットの周辺分布とし、コスト関数 `c` が $c(x, y) = h(|x - y|)$ の形であるモンジュ-カントロビッチ問題の最適輸送コストを計算します。ここで、$h$ は凸関数です。

この設定では、最適輸送計画を解析的に計算できます。結果はスパース行列として返されます。

参照: [`ot_cost`](@ref), [`emd`](@ref)
