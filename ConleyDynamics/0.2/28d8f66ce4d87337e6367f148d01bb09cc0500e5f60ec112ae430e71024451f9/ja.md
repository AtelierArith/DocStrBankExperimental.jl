```
relative_homology(lc::LefschetzComplex,subc::Cells)
```

Lefschetz複体の相対ホモロジーを、部分複体に関して計算します。この計算は、Lefschetz境界行列に関連付けられた体上で行われます。

部分複体は、`subc`内のセルの閉包であり、インデックスまたはラベルのいずれかで与えることができます。ホモロジーは、ベッティ数のベクトル`betti`として返され、ここで`betti[k]`は次元`k-1`のベッティ数です。
