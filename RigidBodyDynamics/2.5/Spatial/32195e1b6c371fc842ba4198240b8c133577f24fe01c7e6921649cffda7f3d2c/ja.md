```julia
struct FreeVector3D{V<:(AbstractVector)}
```

`FreeVector3D`は[自由ベクトル](https://en.wikipedia.org/wiki/Euclidean_vector#Overview)を表します。

自由ベクトルの例には、点の変位や速度が含まれます。

`FreeVector3D`に`Transform3D`を適用すると、`FreeVector3D`は回転するだけです。
