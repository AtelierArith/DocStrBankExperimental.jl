```
ChristoffelSymbol(DM::DataModel, θ::AbstractVector; BigCalc::Bool=false)
ChristoffelSymbol(Metric::Function, θ::AbstractVector; BigCalc::Bool=false)
```

点 $\theta$ での $(1,2)$ クリストッフェル記号 $\Gamma$ の成分を計算します（すなわち、クリストッフェル記号「第二種」）を `Metric` の有限差分を通じて。精度は約 3e-11 です。 `BigCalc=true` は `BigFloat` 計算を通じて精度を向上させます。
