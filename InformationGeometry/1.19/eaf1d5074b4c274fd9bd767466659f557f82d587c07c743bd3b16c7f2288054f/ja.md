```
Riemann(DM::DataModel, θ::AbstractVector; BigCalc::Bool=false)
Riemann(Metric::Function, θ::AbstractVector; BigCalc::Bool=false)
```

$$
(1,3)
$$

リーマンテンソルの成分を `Metric` の有限差分によって計算します。`BigCalc=true` は BigFloat 計算を通じて精度を向上させます。
