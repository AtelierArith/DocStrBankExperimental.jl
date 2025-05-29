```
create_RTLinvR(cache::BasicILMCache[;scale=1.0])
```

提供されたキャッシュ `cache` を使用して、データ型 `ScalarData` を同じ型のデータにマッピングする正方行列 $-R^T L^{-1}R$ を構築します。演算子 `R^T` と `R` はそれぞれ [`interpolate!`](@ref) と [`regularize!`](@ref) に対応し、`L^{-1}` はグリッドラプラシアンの逆行列です。オプションのキーワード `scale` は、行列を指定された値で乗算します。
