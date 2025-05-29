```
correlation(covar::ForwardCovariance, index_1::Integer, index_2::Integer)
correlation(covar::ForwardCovariance, id1::Symbol, id2::Symbol)
```

2つの `ItoIntegral` の相関を期間にわたって取得します。

### 入力

  * `covar` - 相関を求めたい `ForwardCovariance`。
  * `index_1` または `id1` - 興味のある最初の ito のキー/インデックス
  * `index_2` または `id2` - 興味のある2番目の ito のキー/インデックス

### 返り値

  * スカラー
