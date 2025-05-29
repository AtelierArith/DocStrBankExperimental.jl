```
cov(lse::LinearShrinkage, X, [weights::FrequencyWeights]; dims=1, mean=nothing)
```

行列 `X` に沿った次元 `dims` の線形収縮共分散推定器。`lse` によって説明された方法を使用して計算されます。

オプションで、`X` の各観測に関連付けられた `weights` を提供します（`StatsBase.FrequencyWeights` を参照）。

!!! note
    収縮推定における重みの使用に関する理論的ガイダンスは乏しいようです。`FrequencyWeights` は簡単な実装を持っていますが、他の `AbstractWeight` サブタイプのサポートは分析的な正当化を待っています。

