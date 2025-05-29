```
normals(primitive)
```

ジオメトリの法線を返します。

これは遅延イテレータを返すことが許可されています。`decompose_normals(ConcreteVecType, geometry)`を使用して、`ConcreteVecType`が`Vec3f`のようなものである`Vector{ConcreteVecType}`を取得します。
