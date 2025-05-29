```
makemesh(poly::ConvexPolygon{N, T}, ::Int = 0) where {N, T<:Real} -> TriangleMesh
```

ポリゴンのエッジを反復処理し、各エッジの重心を三角形の第三の頂点として使用することで、レンダリング可能な三角形メッシュを作成します。
