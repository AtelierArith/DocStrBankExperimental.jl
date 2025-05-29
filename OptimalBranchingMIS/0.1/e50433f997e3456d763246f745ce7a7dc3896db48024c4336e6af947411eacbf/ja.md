```
mis_size(g::AbstractGraph; branching_strategy::BranchingStrategy = BranchingStrategy(table_solver = TensorNetworkSolver(), selector = MinBoundaryHighDegreeSelector(2, 6, 0), measure=D3Measure()), reducer::AbstractReducer = MISReducer(), show_progress::Bool = false)
```

与えられたグラフの最大独立集合（MIS）のサイズを計算します。

### 引数

  * `g::AbstractGraph`: MISサイズを計算するグラフ。

### キーワード引数

  * `branching_strategy::BranchingStrategy`: （オプション）使用する分岐戦略。デフォルトは、`table_solver=TensorNetworkSolver`、`selector=MinBoundaryHighDegreeSelector(2, 6, 0)`、および`measure=D3Measure`を使用する戦略です。
  * `reducer::AbstractReducer`: （オプション）適用されるリデューサー。デフォルトは`MISReducer`です。
  * `show_progress::Bool`: （オプション）分岐および削減プロセスの進行状況を表示するかどうか。デフォルトは`false`です。

### 戻り値

  * 与えられたグラフの最大独立集合のサイズを表す整数。
