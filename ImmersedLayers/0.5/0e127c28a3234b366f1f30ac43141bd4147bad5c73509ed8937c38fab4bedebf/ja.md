```
InterpolationMatrix(cache::BasicILMCache,src::GridData,trg::PointData)
```

グリッドデータのタイプ `src` をポイントデータのタイプ `trg` に正則化するための補間行列を作成します。（`src` と `trg` はどちらも `cache` のグリッドとポイントに適切なサイズでなければなりません。）
