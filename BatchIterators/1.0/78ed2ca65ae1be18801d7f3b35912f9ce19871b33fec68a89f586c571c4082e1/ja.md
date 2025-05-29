```
choose_batchsize(d, n; maxmemGB = 1.0, maxbatchsize = 2^14, sizeoneB = d*sizeof(Float64))
```

バッチのサイズ（列数）を計算します。これにより、バッチの各列は、`maxmemGB`（ギガバイト）で制約された合計メモリを持つ`sizeoneB`（バイト単位）のサイズのベクトルに変換できます。
