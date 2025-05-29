```
TV <: AbstractRegularizer
```

アイソトロピック全変動を使用した正則化器

# フィールド

  * `hyperparameter::Number`: 正則化器のハイパーパラメータ
  * `weight`: 多次元画像に使用される可能性のある正則化器の重み。
  * `domain::AbstractRegularizerDomain`: 正則化関数が計算される画像ドメイン。
