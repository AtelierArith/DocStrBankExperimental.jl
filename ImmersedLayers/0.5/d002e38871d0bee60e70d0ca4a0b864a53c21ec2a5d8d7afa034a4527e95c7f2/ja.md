```
inverse_laplacian!(w::GridData,sys::ILMSystem)
```

グリッドデータ `w` のインプレース逆ラプラス演算子を計算し、`sys` が `IndexScaling` を持つか `GridScaling` を持つかに応じて、結果に1またはグリッドセルサイズを掛けます。
