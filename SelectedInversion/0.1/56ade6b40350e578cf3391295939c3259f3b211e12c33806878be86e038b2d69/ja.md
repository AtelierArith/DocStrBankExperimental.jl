```
SupernodalMatrix(
    F::SparseArrays.CHOLMOD.Factor;
    transpose_chunks = false,
    symmetric_access = false,
    depermuted_access = false,
)
```

スーパーノーダル Cholesky 因子分解から `SupernodalMatrix` を構築します。

キーワード引数は `SupernodalMatrix` のドキュメントに説明されています。
