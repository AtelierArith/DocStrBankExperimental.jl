```
Adaboost(
  Dict(
    :output => :class,
    :num_iterations => 7
  )
)
```

Adaboostされた決定木スタンプ。詳細は[DecisionTree.jlのドキュメント](https://github.com/bensadeghi/DecisionTree.jl)を参照してください。

ハイパーパラメータ:

  * `:num_iterations` => 7 (AdaBoostの反復回数)

`fit!`、`transform!`を実装しています。
