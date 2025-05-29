```
barabasi_albert!(g, n::Int, k::Int; seed::Int = -1)
```

グラフ `g` を [Barabási–Albert](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model) プロセスに従って `n` 頂点を持つグラフに成長させます。各ステップで新しい頂点が、グラフに既に存在する `k` 個の異なる頂点に優先的に接続されます。

関連情報として [`barabasi_albert`](@ref) を参照してください。
