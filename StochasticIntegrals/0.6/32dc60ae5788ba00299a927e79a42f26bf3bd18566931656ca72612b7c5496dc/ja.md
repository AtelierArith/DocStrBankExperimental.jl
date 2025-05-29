```
covariance(ito1::ItoIntegral,ito2::ItoIntegral, from::Real, to::Real, gaussian_correlation::Real)
covariance(ito1::ItoIntegral,ito2::ItoIntegral, base::Union{Date,DateTime}, from::Union{Date,DateTime}, to::Union{Date,DateTime}, gaussian_correlation::Real)
```

2つの `ItoIntegral` の共分散を、基礎となるブラウン運動が `gaussian_correlation` の相関を持つ期間にわたって取得します。

### 入力

  * `ito1` - 最初の `ItoIntegral`
  * `ito2` - 2番目の `ItoIntegral`
  * `from` - 期間の開始
  * `to` - 期間の終了
  * `gaussian_correlation` - 2つのイートのブラウン運動間の相関。この値は [-1,1] の範囲である必要があります。
  * `on` - どの瞬間のボラティリティを求めますか。

### 出力

  * スカラー
