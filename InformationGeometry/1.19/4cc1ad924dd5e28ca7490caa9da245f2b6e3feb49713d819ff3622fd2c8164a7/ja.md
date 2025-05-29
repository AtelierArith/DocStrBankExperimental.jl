```
Ricci(DM::DataModel, θ::AbstractVector; BigCalc::Bool=false)
Ricci(Metric::Function, θ::AbstractVector; BigCalc::Bool=false)
```

$$
(0,2)
$$

リッチテンソルの成分を `Metric` の有限差分によって計算します。`BigCalc=true` は `BigFloat` 計算を通じて精度を向上させます。
