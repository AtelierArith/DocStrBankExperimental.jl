```
AcquistionData(kdata::Array{T,6})
```

6次元のゼロで埋められたk空間から作成されたAcquisitionData構造体を返します: [x,y,z,channels,echoes,repetitions]

異なるアンダーサンプリングパターンは**エコー次元**に沿ってのみ処理できます。

このメソッドは、データが3次元カルテシアンシーケンスでエンコードされた単一のボリュームに対応していることを前提としています。
