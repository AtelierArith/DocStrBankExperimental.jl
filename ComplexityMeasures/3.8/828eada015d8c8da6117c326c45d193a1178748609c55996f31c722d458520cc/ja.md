```
entropy_approx(x; m = 2, τ = 1, r = 0.2 * Statistics.std(x), base = MathConstants.e)
```

時系列 `x` の近似エントロピー (Pincus, 1991) を計算するための便利な構文です。

これは `complexity(ApproximateEntropy(; m, τ, r, base), x)` のラッパーに過ぎません (詳細は [`ApproximateEntropy`](@ref) を参照)。
