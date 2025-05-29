```
GMM(
    estimator::CovarianceMatrixEstimator
    verbose::Bool = DEFAULT_VERBOSE
    rng::AbstractRNG = Random.GLOBAL_RNG
    tolerance::Real = DEFAULT_TOLERANCE
    max_iterations::Integer = DEFAULT_MAX_ITERATIONS
    decompose_if_fails::Bool = true
)
```

GMMは、基礎となるデータ分布をガウス分布の混合としてモデル化するクラスタリングアルゴリズムです。

# フィールド

  * `estimator`: GMM内の共分散行列を推定するために使用される方法またはアルゴリズムを表します。
  * `verbose`: アルゴリズムが実行中に追加情報を表示するかどうかを制御します。
  * `rng`: アルゴリズムによって使用される乱数生成器を表します。
  * `tolerance`: アルゴリズムの収束基準を表します。これは、収束と見なす前に、連続する反復間でモデルの対数尤度に許可される最大の変化を決定します。
  * `max_iterations`: 収束に達していなくても、アルゴリズムが停止する前に実行する最大反復回数を表します。
  * `decompose_if_fails`: 数値的な問題により分解が失敗した場合に、アルゴリズムがコンポーネントの共分散行列を分解し、その固有値を修正しようとするかどうかを決定します。

# 参考文献

  * Dempster, Arthur P., Nan M. Laird, and Donald B. Rubin. 不完全データからの最大尤度推定法。Journal of the royal statistical society: series B (methodological) 39.1 (1977): 1-22.
