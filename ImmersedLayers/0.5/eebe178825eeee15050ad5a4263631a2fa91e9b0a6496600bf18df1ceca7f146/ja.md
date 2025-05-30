```
inverse_laplacian!(sol::GridData,rhs::GridData,cache::BasicILMCache)
```

グリッドデータ `rhs` の逆ラプラス演算子を計算し、`cache` が `IndexScaling` または `GridScaling` のいずれかに応じて、結果を単位またはグリッドセルサイズで乗算し、結果を `sol` として返します。
