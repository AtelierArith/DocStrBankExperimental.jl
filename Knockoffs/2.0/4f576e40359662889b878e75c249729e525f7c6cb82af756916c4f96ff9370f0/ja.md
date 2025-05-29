```
modelX_gaussian_knockoffs(X::Matrix, method::Symbol; [m], [covariance_approximator], [kwargs...])
modelX_gaussian_knockoffs(X::Matrix, method::Symbol, μ::Vector, Σ::Matrix; [m], [kwargs...])
```

条件付き多変量正規分布から逐次的にサンプリングすることによって、モデルフリーの多変量正規ノックオフを作成します。真の平均 `μ` と共分散 `Σ` は、提供されていない場合はデータから推定されます。

# 入力

  * `X`: 各行がサンプルで、各列が共変量の `n × p` 数値行列。
  * `method`: 次のいずれかの値を取ることができます。

      * `:mvr` 最小分散に基づく再構成可能性ノックオフ（ref 2のアルゴリズム1）
      * `:maxent` 最大エントロピーのノックオフ（ref 2のアルゴリズム2）
      * `:equi` 等距離ノックオフ（ref 1の式2.3）
      * `:sdp` SDPノックオフ（ref 1の式2.4）
      * `:sdp_ccd` 座標降下法によるSDPノックオフ（ref 3のアルゴリズム2.2）
  * `μ`: `X`の列平均の `p × 1` ベクトル、デフォルトは列平均。
  * `Σ`: `X`の共分散の `p × p` 行列、デフォルトは `covariance_approximator` で指定された収縮推定器。
  * `m`: 生成する変数ごとのノックオフコピーの数、デフォルトは1。
  * `covariance_approximator`: 共分散推定器、デフォルトは `LinearShrinkage(DiagonalUnequalVariance(), :lw)` で、p>nの場合に良好な経験的性能を示す傾向があります。詳細なオプションについてはCovarianceEstimation.jlを参照してください。
  * `kwargs...`: `method`で指定されたソルバーへの可能なオプション入力、[`solve_MVR`](@ref)、[`solve_max_entropy`](@ref)、および[`solve_sdp_ccd`](@ref)を参照してください。

# 参考文献:

1. "Panning for Gold: Model-X Knockoffs for High-dimensional Controlled Variable Selection" by Candes, Fan, Janson, and Lv (2018)
2. "Powerful knockoffs via minimizing reconstructability" by Spector, Asher, and Lucas Janson (2020)
3. "FANOK: Knockoffs in Linear Time" by Askari et al. (2020).

# 共分散近似:

共分散は、`DiagonalUnequalVariance` ターゲットを使用した線形収縮推定器によって近似され、`p>n` の場合に良好に機能するようです。`isposdef(cov(X))` が通常は偽であるため、単に `cov(X)` を使用することはありません。さまざまな推定器の比較については、https://mateuszbaran.github.io/CovarianceEstimation.jl/dev/man/msecomp/#msecomp を参照してください。
