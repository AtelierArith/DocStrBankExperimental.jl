```
pointwise_cross!(C::VectorData,A::ScalarData/VectorData,B::VectorData/ScalarData) -> VectorData
```

点データ `A` と `B` の間のクロス積を計算します。これらのうちの一つはスカラー データで、ベクトルの面外成分として扱われ、もう一つは面内ベクトル データです。結果はベクトル データ `C` として返されます。
