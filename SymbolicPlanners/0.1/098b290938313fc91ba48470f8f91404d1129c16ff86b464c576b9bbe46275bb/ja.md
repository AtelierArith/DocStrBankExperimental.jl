```
BiPathSearchSolution(status, plan)
BiPathSearchSolution(status, plan, trajectory)
BiPathSearchSolution(status, plan, trajectory, expanded,
                     f_search_tree, f_frontier, f_expanded, f_trajectory,
                     b_search_tree, b_frontier, b_expanded, b_trajectory)
```

双方向探索ベースのプランナーのためのソリューションタイプ。

# フィールド

  * `status`: 返されたソリューションのステータス。
  * `plan`: 目標に到達するためのアクションのシーケンス。部分的または不完全である可能性があります。
  * `trajectory`: プランに従って移動する際に通過する状態の軌跡。
  * `expanded`: 探索中に拡張されたノードの数。
  * `f_search_tree`: 前方探索ツリー。
  * `f_frontier`: 前方探索フロンティア。
  * `f_expanded`: 前方探索を通じて拡張されたノードの数。
  * `f_trajectory`: 前方探索によって返された状態の軌跡。
  * `b_search_tree`: 後方探索ツリー。
  * `b_frontier`: 後方探索フロンティア。
  * `b_expanded`: 後方探索を通じて拡張されたノードの数。
  * `b_trajectory`: 後方探索によって返された状態の軌跡。
