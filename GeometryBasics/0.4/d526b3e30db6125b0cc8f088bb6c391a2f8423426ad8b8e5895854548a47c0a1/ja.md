```
coordinates(geometry)
```

ジオメトリのエッジ/頂点/座標を返します。遅延イテレータを返すことも許可されています！ `decompose(ConcretePointType, geometry)` を使用して、`ConcretePointType` を `Point{3, Float32}` のようなものにする `Vector{ConcretePointType}` を取得します。
