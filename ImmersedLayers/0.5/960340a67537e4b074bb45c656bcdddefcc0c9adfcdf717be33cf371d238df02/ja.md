```
RegularizationMatrix(cache::BasicILMCache,src::PointData,trg::GridData)
```

ポイントデータのタイプ `src` をグリッドデータのタイプ `trg` に正則化するための正則化行列を作成します。（`src` と `trg` は両方とも `cache` のグリッドとポイントに適切なサイズである必要があります。）
