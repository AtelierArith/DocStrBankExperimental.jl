```
texturecoordinates(primitive)
```

ジオメトリのテクスチャ座標を返します。

これは遅延イテレータを返すことが許可されています。`decompose_uv(ConcreteVecType, geometry)`（または`decompose_uvw`）を使用して、`ConcreteVecType`が`Vec2f`のようなものである`Vector{ConcreteVecType}`を取得します。
