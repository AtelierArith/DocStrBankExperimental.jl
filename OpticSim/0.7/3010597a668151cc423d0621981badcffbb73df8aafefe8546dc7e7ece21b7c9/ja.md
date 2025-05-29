```
makemesh(object, subdivisions::Int = 30) -> TriangleMesh
```

オブジェクトから[`TriangleMesh`](@ref)を作成します。オブジェクトは、[`ParametricSurface`](@ref)、[`CSGTree`](@ref)または特定のサーフェス（例：`Circle`、`Rectangle`）である必要があります。これは視覚化の目的のみで使用されます。
