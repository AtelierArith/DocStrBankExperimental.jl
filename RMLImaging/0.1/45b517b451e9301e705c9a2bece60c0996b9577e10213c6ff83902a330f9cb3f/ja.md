```
KLEntropy <: AbstractRegularizer
```

Kullback-Leiblerダイバージェンス（または相対エントロピー）を使用した正則化器。

# フィールド

  * `hyperparameter::Number`: 正則化器のハイパーパラメータ
  * `prior`: 事前画像。
  * `domain::AbstractRegularizerDomain`: 正則化関数が計算される画像ドメイン。KLEntropyは`LinearDomain()`でのみ計算できます。
