```
covariance(covar::ForwardCovariance, index_1::Integer, index_2::Integer)
covariance(covar::ForwardCovariance, id1::Symbol, id2::Symbol)
```

`ForwardCovariance` における2つのイート積分の共分散を取得します。

### 入力

  * `covar` - 共分散を取得したい `ForwardCovariance`。
  * `index_1` または `id1` - 興味のある最初のイートのキー/インデックス
  * `index_2` または `id2` - 興味のある2番目のイートのキー/インデックス

### 戻り値

  * スカラー
