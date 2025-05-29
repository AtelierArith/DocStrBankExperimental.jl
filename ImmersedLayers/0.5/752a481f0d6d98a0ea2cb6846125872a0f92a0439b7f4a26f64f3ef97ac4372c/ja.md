```
create_CLinvCT_scalar(cache::BasicILMCache[;scale=1.0])
```

提供されたキャッシュ `cache` を使用して、スカラー点データ型のデータを同じ型のデータにマッピングする正方行列 $-C_s L^{-1}C_s^T$ を構築します。演算子 `C_s` と `C_s^T` は [`surface_curl!`](@ref) に対応し、`L` はグリッドラプラシアンです。オプションのキーワード `scale` は、行列を指定された値で乗算します。
