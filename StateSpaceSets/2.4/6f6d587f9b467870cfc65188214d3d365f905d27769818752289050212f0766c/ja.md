```
Centroid(metric = Euclidean())
```

[`set_distance`](@ref)で使用できる距離です。`Centroid`メソッドは、セットの[重心](https://en.wikipedia.org/wiki/Centroid)（すなわち質量の中心）間の距離（`metric`に従って）を返します。

`metric`は、2つの静的ベクトルを受け取り、距離として使用するための正定値数を返す任意の関数であることができます（通常はDistances.jlの`Metric`です）。
