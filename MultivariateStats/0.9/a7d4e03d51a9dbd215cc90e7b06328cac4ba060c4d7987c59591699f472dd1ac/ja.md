```
predict(M::KernelPCA, x)
```

モデル `M` のカーネル空間における `x` のサンプル外変換を行います。

ここで、`x` は長さ `d` のベクトルまたは各列が観測値である行列のいずれかです。
