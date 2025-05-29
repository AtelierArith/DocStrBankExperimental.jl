```
homology(lc::LefschetzComplex)
```

Lefschetz複体のホモロジーを計算します。

ホモロジーは、ベッティ数のベクトル `betti` として返されます。ここで、`betti[k]` は次元 `k-1` のベッティ数です。計算は、Lefschetz複体の境界行列に関連付けられた体上で行われます。
