```julia
struct GradientGrassmann{O<:OptimKit.OptimizationAlgorithm, F} <: MPSKit.Algorithm
```

変分勾配ベースの最適化アルゴリズムで、MPSを左正準形のまま保持し、グラスマン多様体上の点として扱います。最適化は、ヒルベルト空間内積からメトリックを誘導するための前処理器を用いたリーマン勾配降下法です。

## フィールド

  * `method::OptimKit.OptimizationAlgorithm`: 最適化アルゴリズム
  * `finalize!::Any`: 各イテレーション後に適用されるコールバック関数で、シグネチャは `finalize!(x, f, g, numiter) -> x, f, g`

## 参考文献

  * [Hauru et al. SciPost Phys. 10 (2021)](@cite hauru2021)

---

## コンストラクタ

```
GradientGrassmann(; kwargs...)
```

### キーワード

  * `method=ConjugateGradient`: 最適化アルゴリズムのインスタンス、または構築する最適化アルゴリズムのタイプ
  * `finalize!`: ファイナライザーアルゴリズム
  * `tol::Float64`: 収束基準の許容誤差
  * `maxiter::Int`: 最大イテレーション数
  * `verbosity::Int`: 情報表示のレベル
