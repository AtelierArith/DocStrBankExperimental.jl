```julia
mutable struct Mesh{T} <: ConstrainedDynamics.Shape{T}
```

`Mesh`は任意のジオメトリを視覚化するために使用できます。

# 重要な属性

  * `path`: ジオメトリファイルへのパス。
