```
inverse_laplacian!(w::GridData,cache::BasicILMCache)
```

グリッドデータ `w` のインプレース逆ラプラス演算を計算し、`cache` が `IndexScaling` を持つか `GridScaling` を持つかに応じて、結果に1またはグリッドセルサイズを掛けます。
