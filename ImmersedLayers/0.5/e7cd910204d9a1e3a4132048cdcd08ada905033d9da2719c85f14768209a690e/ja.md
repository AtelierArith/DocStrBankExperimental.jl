```
create_GLinvD_cross(cache::BasicILMCache[;scale=1.0])
```

提供されたキャッシュ `cache` を使用して、データ型 `ScalarData` を同じ型のデータにマッピングする正方行列 $-\hat{G}_s L^{-1}\hat{D}_s$ を構築します。演算子 `G_s` と `D_s` はそれぞれ [`surface_grad_cross!`](@ref) と [`surface_divergence_cross!`](@ref) に対応し、`L` はグリッドラプラシアンです。オプションのキーワード `scale` は、行列を指定された値で乗算します。
