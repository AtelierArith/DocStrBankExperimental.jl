```
ot_cost(
    c, μ::DiscreteNonParametric, ν::DiscreteNonParametric; plan=nothing
)
```

離散一変量分布 `μ` と `ν` をソースおよびターゲットの周辺分布とし、コスト関数 `c` が $c(x, y) = h(|x - y|)$ の形であるモンジュ＝カントロビッチ問題の最適輸送コストを計算します。ここで、$h$ は凸関数です。

この設定では、最適輸送コストを解析的に計算できます。

事前に計算された最適輸送 `plan` を提供することができます。

参照: [`ot_plan`](@ref), [`emd2`](@ref)
