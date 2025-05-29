```
L1Norm <: AbstractRegularizer
```

l1ノルムを使用した正則化器。

# フィールド

  * `hyperparameter::Number`: 正則化器のハイパーパラメータ
  * `weight`: 正則化器の重みで、数値または配列である可能性があります。
  * `domain::AbstractRegularizerDomain`: 正則化関数が計算される画像ドメイン。L1Normは`LinearDomain()`でのみ計算できます。
