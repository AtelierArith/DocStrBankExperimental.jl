```
RandomSwap(
    local_search::AbstractAlgorithm
    verbose::Bool = DEFAULT_VERBOSE
    max_iterations::Integer = 200
    max_iterations_without_improvement::Integer = 150
)
```

RandomSwapはクラスタリング問題に使用されるメタヒューリスティックアプローチです。これは、探索空間を効果的に探索するために、局所最適化と摂動を組み合わせた反復プロセスに従います。各反復で局所最適化アルゴリズムが適用され、局所最適解に収束します。その後、摂動オペレーターが新しい出発点を生成し、探索を続けます。

# フィールド

  * `local_search`: 各メタヒューリスティック反復で解を改善するために適用されるクラスタリングアルゴリズム。
  * `verbose`: アルゴリズムが実行中に追加情報を表示するかどうかを制御します。
  * `max_iterations`: アルゴリズムが停止する前に実行する最大反復回数を表します。
  * `max_iterations_without_improvement`: 最良の解を改善せずに許可される最大反復回数を表します。

# 参考文献

  * Fränti, Pasi. Efficiency of random swap clustering. Journal of big data 5.1 (2018): 1-29.
