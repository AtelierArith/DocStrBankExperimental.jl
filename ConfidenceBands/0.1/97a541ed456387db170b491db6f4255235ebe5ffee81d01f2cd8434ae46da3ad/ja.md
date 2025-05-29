```
criticalvalue(cb::PlugInConfidenceBand, level::Real, Σ::AbstractMatrix)
```

`cb`の臨界値を、推定された分散共分散行列`Σ`を持つときの信頼水準`level`で返します。いくつかのタイプのプラグイン信頼帯では、`Σ`の代わりにポイント推定の数を提供するだけで十分です。
