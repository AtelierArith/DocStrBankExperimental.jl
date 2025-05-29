```
transformation(c::GeometryStructure, d::GeometryReference)
```

`c`という`GeometryStructure`がその参照のツリーに`d`という[`GeometryReference`](@ref)を含んでいる場合、この関数は`d`の座標系から`c`の座標系に変換するための`Transformations.ScaledIsometry`オブジェクトを返します。

*まったく同じ* `GeometryReference`（`===`、メモリ内の同じアドレス）が参照のツリーに複数回含まれている場合、結果の変換は最初に遭遇したときに基づきます。ツリーは参照を見つけるために1レベルずつトラバースされます（浅い参照に最適化されています）。

例：参照された座標系`d`の座標系で(2.0,3.0)を`c`の座標系に変換したい場合：

```
julia> trans = transformation(c,d)

julia> trans(Point(2.0,3.0))
```
