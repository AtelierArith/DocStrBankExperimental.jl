```
pointwise_cross!(C::VectorData,A::ScalarData/VectorData,B::VectorData/ScalarData) -> VectorData
```

点データ `A` と `B` の間のクロス積を計算します。どちらか一方はスカラー データで、ベクトルの面外成分として扱われ、もう一方は面内ベクトル データです。結果はベクトル データ `C` として返されます。
