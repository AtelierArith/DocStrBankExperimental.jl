```
planner = BidirectionalPlanner(;
    forward::ForwardPlanner = ForwardPlanner(),
    backward::BackwardPlanner = BackwardPlanner(),
    max_nodes::Int = typemax(Int),
    max_time::Float64 = Inf,
    save_search::Bool = false
)
```

初期状態から前方探索を、目標から後方探索を同時に実行する双方向プランナーであり、いずれかの探索が成功するか、探索のフロンティアが交差していることが検出されれば成功します。

フロンティアの交差は、最も最近拡張された前方ノードが後方探索フロンティアのノードに包含されているか、またはその逆を確認することで検出されます。包含とは、後方ノードによって表される部分状態が前方ノードによって表される完全状態と一致していることを意味します。

上記の手続きは完全ではありません（すなわち、一部の交差が見逃される可能性があります）が、包含をテストするコストと交差を検出する利益との間のトレードオフを表しています。より洗練された方法に代わるものです [1]。

[1] V. Alcázar, S. Fernández, and D. Borrajo, "Analyzing the Impact of Partial States on Duplicate Detection and Collision of Frontiers," ICAPS (2014), [https://doi.org/10.1609/icaps.v24i1.13677](https://doi.org/10.1609/icaps.v24i1.13677)

# 引数

  * `forward`: 前方探索の設定。
  * `backward`: 後方探索の設定。
  * `max_nodes`: 終了前の最大探索ノード数。
  * `max_time`: プランナーがタイムアウトするまでの最大時間（秒）。
  * `save_search`: 返された解に探索ツリーとフロンティアを保存するフラグ。
