```
relative_homology(lc::LefschetzComplex,subc::Cells,subc0::Cells)
```

Lefschetz複体に対する部分複体に関する相対ホモロジーを計算します。この計算は、Lefschetz境界行列に関連付けられた体上で行われます。

この実装では、ペア `cl(subc), cl(subc0))` の相対ホモロジーが計算されます。`cl(subc0)` が `cl(subc)` の部分集合でない場合、エラーが発生します。ホモロジーは、ベッティ数のベクトル `betti` として返され、ここで `betti[k]` は次元 `k-1` のベッティ数です。
