```
faces(geometry)
```

ジオメトリの面を返します。

これは遅延イテレータを返すことができます。`decompose(ConcreteFaceType, geometry)`を使用して、`ConcreteFaceType`が`GLTriangleFace`のようなものである`Vector{ConcreteFaceType}`を取得します。
