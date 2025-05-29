```
prob(s::EpsilonGreedyExplorer, values) ->Categorical
prob(s::EpsilonGreedyExplorer, values, mask) ->Categorical
```

各アクションの推定された `values` に基づいて、各アクションを選択する確率を返します。
