```
TSV <: AbstractRegularizer
```

アイソトロピック全二乗変動を使用した正則化器

# フィールド

  * `hyperparameter::Number`: 正則化器のハイパーパラメータ
  * `weight`: 正則化器の重みであり、多次元画像に使用される場合があります。
  * `domain::AbstractRegularizerDomain`: 正則化関数が計算される画像ドメイン。
