```
entropy_sample(x; r = 0.2std(x), m = 2, τ = 1, normalize = true)
```

時系列 `x` の（正規化された）サンプルエントロピー（Richman & Moorman, 2000）を推定するための便利な構文です。

これは `complexity(SampleEntropy(; r, m, τ, base), x)` のラッパーに過ぎません。

関連情報: [`SampleEntropy`](@ref), [`complexity`](@ref), [`complexity_normalized`](@ref)）。
