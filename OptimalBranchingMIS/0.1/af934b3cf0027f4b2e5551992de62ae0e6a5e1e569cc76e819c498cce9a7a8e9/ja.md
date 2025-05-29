```
mis_branch_count(g::AbstractGraph; branching_strategy::BranchingStrategy = BranchingStrategy(table_solver = TensorNetworkSolver(), selector = MinBoundaryHighDegreeSelector(2, 6, 0), measure=D3Measure()), reducer=MISReducer(), show_progress::Bool = false)
```

与えられたグラフの最大独立集合（MIS）のサイズと分岐の数を計算します。

### 引数

  * `g::AbstractGraph`: MISのサイズと分岐の数を計算するグラフ。

### キーワード引数

  * `branching_strategy::BranchingStrategy`: （オプション）使用する分岐戦略。デフォルトは、`table_solver=TensorNetworkSolver`、`selector=MinBoundaryHighDegreeSelector(2, 6, 0)`、および`measure=D3Measure`を使用する戦略です。
  * `reducer::AbstractReducer`: （オプション）適用されるリデューサー。デフォルトは`MISReducer`です。
  * `show_progress::Bool`: （オプション）分岐および削減プロセスの進行状況を表示するかどうか。デフォルトは`false`です。

### 戻り値

  * `(size, count)`というタプルを返します。ここで、`size`は最大独立集合のサイズ、`count`は分岐の数です。
