```
struct TensorNetworkReducer <: AbstractReducer
```

テンソルネットワーク収縮を使用して削減ルールを見つけるリデューサ。

# フィールド

  * `n_max::Int = 15`: 選択された領域に含める最大頂点数
  * `selector::Symbol = :mincut`: 頂点を収縮するための選択戦略。オプションは次のとおりです：

      * `:neighbor`: 隣接に基づいて頂点を選択
      * `:mincut`: `KaHyPar`によって提供される最小カットに基づいて頂点を選択（拡張として、`using KaHyPar`が必要）！注意：`KaHyPar`はメモリリークを引き起こす可能性があります！
  * `measure::AbstractMeasure = NumOfVertices()`: カーネル化に使用される測定。OptimalBranchingMISからのサイズ削減を使用
  * `intersect_strategy::Symbol = :bfs`: 節の交差に関する戦略。オプションは次のとおりです：

      * `:bfs`: 幅優先探索（最適な結果を提供）
      * `:dfs`: 深さ優先探索（最初に見つかった非ゼロ交差を提供）
  * `sub_reducer::AbstractReducer = XiaoReducer()`: テンソルネットワーク収縮の前に選択された頂点に適用されるリデューサ、デフォルトはXiaoReducer
