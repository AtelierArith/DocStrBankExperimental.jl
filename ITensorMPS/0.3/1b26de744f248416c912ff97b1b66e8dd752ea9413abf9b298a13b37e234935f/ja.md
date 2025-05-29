```
product(P::ProjMPOSum,v::ITensor)

(P::ProjMPOSum)(v::ITensor)
```

ProjMPOSum `P` を ITensor `v` に効率的に掛け算します。ここで、ProjMPOSum は一般化された正方行列または線形演算子であり、`v` はそれが作用する空間における一般化されたベクトルです。返される ITensor は `v` と同じインデックスを持ちます。演算子オーバーロード `P(v)` は `product(P,v)` の短縮形です。
