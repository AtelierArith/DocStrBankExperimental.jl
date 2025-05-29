```
MeshCell <: AbstractMeshCell
```

非構造または多角形グリッドの単一セル要素。

これは、セルタイプ（例えば、`VTKCellType.TRIANGLE`や`PolyData.Strips`）と、このセルを定義するグリッド上の点を決定する接続ベクトルによって特徴付けられます。

---

```
MeshCell(cell_type, connectivity)
```

非構造グリッドの単一セル要素を定義します。

`cell_type`引数はセルのタイプ（例：頂点、三角形、六面体など）を特徴付けます：

  * 非構造データセットのセルタイプは[`VTKCellTypes`](@ref)モジュールで定義されています;
  * 多角形データセットのセルタイプは[`PolyData`](@ref)モジュールで定義されています。

`connectivity`引数は、このセルを定義するために`vtk_grid`に渡された点のインデックスを含むベクトルまたはタプルです。

# 例

インデックス`[3, 5, 42]`を持つ点を通る三角形セルを定義します。

```jldoctest
julia> cell = MeshCell(VTKCellTypes.VTK_TRIANGLE, (3, 5, 42))
MeshCell{VTKCellType, Tuple{Int64, Int64, Int64}}(VTKCellType("VTK_TRIANGLE", 0x05, 3), (3, 5, 42))
```
