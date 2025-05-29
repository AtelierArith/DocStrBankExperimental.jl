```
ReusableTreePolicy(
    value_policy::PolicySolution,
    search_sol::PathSearchSolution,
    [goal_tree::Dict{UInt, PathNode}]
)
```

[`RealTimeHeuristicSearch`](@ref)によって返されるポリシーで、ネストされた`value_policy`に価値テーブルを格納し、`search_sol`に前方探索木を持ち、（`reuse_paths`が`true`の場合）目標へのコスト最適パスの再利用可能な`goal_tree`を持ちます。

保存されたコスト最適パスに沿った状態でアクションを取る際には、そのパスに沿ったアクションが実行されます。これはTree-Adaptive A* [1]のように行われます。それ以外の場合、`value_policy`に従って最も価値の高いアクションが返され、同点の場合は`search_sol`内の（不完全な可能性のある）計画によって決定されます。

[1] C. Hernández, X. Sun, S. Koenig, and P. Meseguer, "Tree Adaptive A*,"  AAMAS (2011), pp. 123–130. [https://dl.acm.org/doi/abs/10.5555/2030470.2030488](https://dl.acm.org/doi/abs/10.5555/2030470.2030488).
