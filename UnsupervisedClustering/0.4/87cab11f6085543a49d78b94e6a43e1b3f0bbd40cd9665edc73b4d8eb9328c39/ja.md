```
GeneticAlgorithm(
    local_search::AbstractAlgorithm
    verbose::Bool = DEFAULT_VERBOSE
    max_iterations::Integer = 200
    max_iterations_without_improvement::Integer = 150
    π_min::Integer = 40
    π_max::Integer = 50
)
```

GeneticAlgorithmは、クラスタ割り当てを最適化するために遺伝的アルゴリズムアプローチを利用するクラスタリングアルゴリズムを表します。進化的計算と局所探索要素を組み合わせて、高品質なクラスタリングソリューションを見つけます。

# フィールド

  * `local_search`: 各メタヒューリスティックの反復で解を改善するために適用されるクラスタリングアルゴリズム。
  * `verbose`: アルゴリズムが実行中に追加情報を表示するかどうかを制御します。
  * `max_iterations`: アルゴリズムが停止する前に実行する最大反復回数を表します。
  * `max_iterations_without_improvement`: 最良の解を改善せずに許可される最大反復回数を表します。
  * `π_max`: 遺伝的アルゴリズムで使用される最大人口サイズ。
  * `π_min`: 遺伝的アルゴリズムで使用される最小人口サイズ。

# 参考文献
