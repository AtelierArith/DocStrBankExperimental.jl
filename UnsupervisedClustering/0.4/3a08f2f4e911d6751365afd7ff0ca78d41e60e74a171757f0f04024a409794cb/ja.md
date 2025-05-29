```
Kmedoids(
    verbose::Bool = DEFAULT_VERBOSE
    rng::AbstractRNG = Random.GLOBAL_RNG
    tolerance::Real = DEFAULT_TOLERANCE
    max_iterations::Integer = DEFAULT_MAX_ITERATIONS
)
```

k-medoidsは、平均の代わりに各クラスタの代表として実際のデータポイント（メドイド）を使用するk-meansクラスタリングアルゴリズムのバリエーションです。

# フィールド

  * `verbose`: アルゴリズムが実行中に追加情報を表示するかどうかを制御します。
  * `rng`: アルゴリズムで使用される乱数生成器を表します。
  * `tolerance`: アルゴリズムの収束基準を表します。これは、連続するイテレーション間でセントロイドの位置に許可される最大の変化を決定します。
  * `max_iterations`: 収束が達成されていなくても、アルゴリズムが停止する前に実行する最大のイテレーション数を表します。

# 参考文献
