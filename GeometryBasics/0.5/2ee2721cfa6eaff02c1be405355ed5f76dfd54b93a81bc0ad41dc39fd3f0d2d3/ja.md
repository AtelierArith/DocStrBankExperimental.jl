```
coordinates(geometry)
```

ジオメトリの位置/座標を返します。

これは遅延イテレータを返すことができます。`decompose(ConcretePointType, geometry)`を使用して、`ConcretePointType`が`Point3f`のようなものである`Vector{ConcretePointType}`を取得します。
