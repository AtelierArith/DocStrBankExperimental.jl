```
lowrank_stream(k, d, n, ν = 0.0; out_dic = nothing)
```

`n` 個の `d` 次元ベクトルを `k` 次元部分空間に配置して返す `RandomStreamDataset` を返します。このストリームは `BatchIterator` ラッパーを使用して反復処理できます。
