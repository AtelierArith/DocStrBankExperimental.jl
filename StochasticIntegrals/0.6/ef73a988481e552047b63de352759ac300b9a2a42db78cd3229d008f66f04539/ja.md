```
variance(covar::ForwardCovariance, id::Symbol)
variance(covar::ForwardCovariance, index::Integer)
```

`ForwardCovariance`の期間にわたる分散を取得します。

### 入力

  * `covar` - 分散を求めたい`ForwardCovariance`。
  * `id`または`index` - 興味のあるito辞書のキー/インデックス

### 戻り値

  * スカラー
