```
Kmeans(
    metric::SemiMetric = SqEuclidean()
    verbose::Bool = DEFAULT_VERBOSE
    rng::AbstractRNG = Random.GLOBAL_RNG
    tolerance::Real = DEFAULT_TOLERANCE
    max_iterations::Integer = DEFAULT_MAX_ITERATIONS
)
```

k-meansは、データポイントとそのクラスタセントロイドとの距離を最小化することによってデータをクラスタに分割することを目的としたクラスタリングアルゴリズムです。

# フィールド

  * `metric`: データポイントとクラスタセントロイドとの距離を計算するために使用される距離メトリックを定義します。
  * `verbose`: アルゴリズムが実行中に追加情報を表示するかどうかを制御します。
  * `rng`: アルゴリズムによって使用される乱数生成器を表します。
  * `tolerance`: アルゴリズムの収束基準を表します。これは、連続するイテレーション間でセントロイドの位置に許可される最大の変化を決定します。
  * `max_iterations`: 収束が達成されていなくても、アルゴリズムが停止する前に実行する最大のイテレーション数を表します。

# 参考文献

  * Hartigan, John A., and Manchek A. Wong. Algorithm AS 136: A k-means clustering algorithm. Journal of the royal statistical society. series c (applied statistics) 28.1 (1979): 100-108.
  * Lloyd, Stuart. Least squares quantization in PCM. IEEE transactions on information theory 28.2 (1982): 129-137.
