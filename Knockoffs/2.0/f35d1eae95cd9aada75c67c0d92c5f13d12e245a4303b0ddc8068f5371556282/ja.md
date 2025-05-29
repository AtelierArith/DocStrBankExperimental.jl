```
approx_modelX_gaussian_knockoffs(X, method; [m=1], [windowsize = 500], [covariance_approximator], kwargs...)
approx_modelX_gaussian_knockoffs(X, method, window_ranges; [m=1], [covariance_approximator], kwargs...)
```

ガウスノックオフを生成するために、共分散をブロック対角行列として近似します。各ブロックには `windowsize` の連続した特徴が含まれます。代わりに `window_ranges` 引数を指定して、異なるサイズのブロックを構築することもできます。

# 入力

  * `X`: `n × p` の数値行列または `SnpArray`。各行はサンプルで、各列は共変量です。
  * `method`: 次のいずれかであることができます

      * `:mvr` 最小分散に基づく再構成可能ノックオフ (ref 2のアルゴリズム1)
      * `:maxent` 最大エントロピーのノックオフ (ref 2のアルゴリズム2)
      * `:equi` 等距離ノックオフ (ref 1の式2.3)
      * `:sdp` SDPノックオフ (ref 1の式2.4)
      * `:sdp_fast` 座標降下法によるSDPノックオフ (ref 3のアルゴリズム2.2)
  * `m`: 生成する変数ごとのノックオフコピーの数、デフォルトは1です。
  * `windowsize`: ブロックに含まれる共変量の数。各ブロックは隣接する変数で構成されます。最後のブロックには `windowsize` より少ない変数が含まれる場合があります。
  * `window_ranges`: 各ウィンドウの範囲のベクトル。例: [1:97, 98:200, 201:500]
  * `covariance_approximator`: 共分散推定器、デフォルトは `LinearShrinkage(DiagonalUnequalVariance(), :lw)` です。詳細は CovarianceEstimation.jl を参照してください。
  * `kwargs...`: `method` で指定されたソルバーへの可能なオプション入力、[`solve_MVR`](@ref)、[`solve_max_entropy`](@ref)、および [`solve_sdp_ccd`](@ref) を参照してください。

# マルチスレッド (todo)

複数のスレッドを有効にするには、単に >1 スレッドでJuliaを起動すれば、このルーチンは利用可能なすべてのスレッドで実行されます。

# 共分散近似:

共分散は `LinearShrinkageEstimator` を使用して近似され、`DiagonalUnequalVariance` ターゲットでのLedoit-Wolf収縮が行われます。これは `p>n` のケースでうまく機能するようです。`cov(X)` を単純に使用しないのは、通常 `isposdef(cov(X))` が偽であるためです。異なる推定器の比較については、https://mateuszbaran.github.io/CovarianceEstimation.jl/dev/man/msecomp/#msecomp を参照してください。
