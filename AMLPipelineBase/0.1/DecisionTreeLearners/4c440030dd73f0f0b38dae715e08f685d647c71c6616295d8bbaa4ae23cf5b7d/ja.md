```
PrunedTree(
  Dict(
    :purity_threshold => 1.0,
    :max_depth => -1,
    :min_samples_leaf => 1,
    :min_samples_split => 2,
    :min_purity_increase => 0.0
  )
)
```

決定木分類器。   [DecisionTree.jlのドキュメント](https://github.com/bensadeghi/DecisionTree.jl)を参照してください。

ハイパーパラメータ:

  * `:purity_threshold` => 1.0 (結合された純度が>=threshの葉をマージ)
  * `:max_depth` => -1 (決定木の最大深さ)
  * `:min_samples_leaf` => 1 (各葉が持つ必要がある最小サンプル数)
  * `:min_samples_split` => 2 (分割に必要な最小サンプル数)
  * `:min_purity_increase` => 0.0 (分割に必要な最小純度)

`fit!`、`transform!`を実装します。
