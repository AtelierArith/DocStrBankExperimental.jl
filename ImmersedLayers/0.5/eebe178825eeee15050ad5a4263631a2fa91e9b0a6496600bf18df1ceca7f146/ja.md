```
inverse_laplacian!(sol::GridData,rhs::GridData,cache::BasicILMCache)
```

グリッドデータ `rhs` の逆ラプラス演算子を計算し、`cache` が `IndexScaling` または `GridScaling` のいずれかに応じて、結果に1またはグリッドセルサイズを掛け、結果を `sol` として返します。
