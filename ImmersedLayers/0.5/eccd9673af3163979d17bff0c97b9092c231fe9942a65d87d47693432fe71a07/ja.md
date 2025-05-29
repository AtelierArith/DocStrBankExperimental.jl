```
create_nRTRn(cache::BasicILMCache[;scale=1.0])
```

提供されたキャッシュ `cache` を使用して、データ型 `ScalarData` を同じ型のデータにマッピングする正方行列 $n\cdot R_f^T R_f n \circ$ を構築します。演算子 `R_f^T` と `R_f` は、それぞれ補間行列と正則化行列に対応します。オプションのキーワード `scale` は、行列を指定された値で乗算します。
