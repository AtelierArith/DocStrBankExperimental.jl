```
isosurface(V)
isosurface(V, method::AbstractMeshingAlgorithm, X, Y, Z)
```

`isosurface` はすべての等値面抽出アルゴリズムへの一般的なインターフェースです。

返り値: (Vector{NTuple{3, T}, }, Vector{NTuple{3, Int}})

デフォルト: `method` は `AbstractMeshingAlgorithm` のインスタンスでなければなりません。例えば：

  * MarchingCubes()
  * MarchingTetrahedra()

`isosurface` が指定されたアルゴリズムなしで呼び出されると、デフォルトで MarchingCubes になります。

`AbstractArray` のサブタイプが指定された場合、メッシュはデフォルトで各軸の間で原点を中心に (-1,1) に配置されます。

参照:

  * [MarchingCubes](@ref)
  * [MarchingTetrahedra](@ref)
