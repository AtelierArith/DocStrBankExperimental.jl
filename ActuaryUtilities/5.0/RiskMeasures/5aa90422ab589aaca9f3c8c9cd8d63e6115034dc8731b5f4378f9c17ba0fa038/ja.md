```
WangTransform(α)::RiskMeasure
WangTransform(α)(risk)::T (where T is the type of values sampled in risk)
```

Wang Transformは、リスク分布の累積分布関数（CDF）を、平均Φ⁻¹(α)および標準偏差1の正規分布を使用して変換する歪みリスク測度です。riskは単変量分布または結果の配列である可能性があります。

WangTransform(α)は、リスク分布に対して呼び出すことができるファンクタを返します。

## パラメータ

  * α: [0,1.0]

文献では、時々λが使用され、$\lambda = \Phi^{-1}(\alpha)$となります。

## 例

```julia-repl
julia> WangTransform(0.95)(rand(1000))
0.8799465543360105

julia> rm = WangTransform(0.95)
WangTransform{Float64}(0.95)

julia> rm(rand(1000))
0.8892245759705852
```

## 参考文献

  * "A Risk Measure That Goes Beyond Coherence", Shaun S. Wang, 2002
