```julia
struct Point3D{V<:(AbstractVector)}
```

`Point3D`は、特定の座標系における位置を表します。

`Point3D`は、[境界ベクトル](https://en.wikipedia.org/wiki/Euclidean_vector#Overview)です。`Point3D`に`Transform3D`を適用すると、`Point3D`は回転し、平行移動します。
