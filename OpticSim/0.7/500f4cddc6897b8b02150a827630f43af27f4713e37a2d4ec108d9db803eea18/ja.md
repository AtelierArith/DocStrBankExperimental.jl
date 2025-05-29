```
uvrange(s::ParametricSurface)
uvrange(::Type{S}) where {S<:ParametricSurface}
```

この関数は、サーフェスタイプのパラメータ化の制限を指定する形のタプル `((umin, umax), (vmin, vmax))` を返します。また、`ParametricSurface` ではないいくつかの `Surface`（例：`Rectangle`）にも実装されています。
