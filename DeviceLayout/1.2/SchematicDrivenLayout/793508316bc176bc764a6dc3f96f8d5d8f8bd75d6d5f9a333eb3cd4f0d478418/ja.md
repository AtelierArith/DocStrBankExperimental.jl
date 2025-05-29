```
transformation(sch::Schematic, node::ComponentNode)
```

与えられたSchematic `sch`がその`SchematicGraph`内に[`ComponentNode`](@ref) `node`を含む場合、この関数はノードの座標系から`sch`のグローバル座標系に変換するための`CoordinateTransformations.Transformation`オブジェクトを返します。

実質的には`DeviceLayout.transformation(::CoordinateSystem, ::CoordSysRef)`のラッパーです。
