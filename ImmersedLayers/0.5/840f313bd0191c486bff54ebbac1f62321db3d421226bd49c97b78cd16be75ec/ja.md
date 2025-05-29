```
create_GLinvD(cache::BasicILMCache[;scale=1.0])
```

提供されたキャッシュ `cache` を使用して、データ型 `ScalarData` を同じ型のデータにマッピングする正方行列 $-G_s L^{-1}D_s$ を構築します。演算子 `G_s` と `D_s` はそれぞれ [`surface_grad!`](@ref) と [`surface_divergence!`](@ref) に対応し、`L` はグリッドラプラシアンです。オプションのキーワード `scale` は、行列を指定された値で乗算します。
