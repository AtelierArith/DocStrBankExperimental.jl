```
AdaBoostStumpClassifier(; n_iterations::Int=10,
                        rng=Random.GLOBAL_RNG)
```

アダブーストされた決定木スタンプ。詳細は[DecisionTree.jlのドキュメント](https://github.com/bensadeghi/DecisionTree.jl)を参照してください。

ハイパーパラメータ:

  * `n_iterations`: アダブーストの反復回数
  * `rng`: 使用する乱数生成器。`Int`である場合、新しい乱数生成器をシードして作成するために使用されます。

`fit!`、`predict`、`predict_proba`、`get_classes`を実装しています。
