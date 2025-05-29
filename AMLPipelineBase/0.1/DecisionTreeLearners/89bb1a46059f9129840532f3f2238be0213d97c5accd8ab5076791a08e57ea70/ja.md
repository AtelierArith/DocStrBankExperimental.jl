```
RandomForest(
  Dict(
    :output => :class,
    :num_subfeatures => 0,
    :num_trees => 10,
    :partial_sampling => 0.7,
    :max_depth => -1
  )
)
```

ランダムフォレスト分類。 [DecisionTree.jlのドキュメント](https://github.com/bensadeghi/DecisionTree.jl)を参照してください。

ハイパーパラメータ:

  * `:num_subfeatures` => 0  （分割ごとにランダムに考慮する特徴の数）
  * `:num_trees` => 10 （トレーニングする木の数）
  * `:partial_sampling` => 0.7 （各木をトレーニングするためのサンプルの割合）
  * `:max_depth` => -1 （決定木の最大深さ）
  * `:min_samples_leaf` => 1 （各葉が持つ必要のある最小サンプル数）
  * `:min_samples_split` => 2 （分割に必要な最小サンプル数）
  * `:min_purity_increase` => 0.0 （分割に必要な最小純度）

`fit!`、`transform!`を実装します。
