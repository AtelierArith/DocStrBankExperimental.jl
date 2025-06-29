```
factorize(F::LUFactor, B::SparseMatrixCSC{Float64, Int64}; check::Bool=true)
```

スパース行列 `B` を因数分解します。`B` は正方行列であり、`F` が作成された次元を持っている必要があります。

因数分解メソッドは、アクティブな部分行列のすべての要素が絶対ピボット許容値未満になると停止します。この場合、`L` および `U` 行列は単位行列の列でパディングされ、依存列が単位行列の列に置き換えられた行列 `B*` の因数分解が得られます。実際に行われたピボットステップの数は、`getinfo(F, :nPivot)` で取得できます。

`check = true` の場合、ピボットステップの数が `B` の次元より少ないとエラーが発生します。
