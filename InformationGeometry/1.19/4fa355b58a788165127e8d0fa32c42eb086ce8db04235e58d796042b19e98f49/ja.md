```
RicciScalar(DM::DataModel, θ::AbstractVector; BigCalc::Bool=false) -> Real
RicciScalar(Metric::Function, θ::AbstractVector; BigCalc::Bool=false) -> Real
```

`Metric`の有限差分によってリッチスカラーを計算します。`BigCalc=true`は`BigFloat`計算を通じて精度を向上させます。
