```
VTKPolyhedron <: AbstractMeshCell
```

非構造グリッドにおける多面体セルを表します。

`VTKPolyhedron`を使用することが、セルタイプ`VTKCellTypes.VTK_POLYHEDRON`の`MeshCell`を使用することよりも推奨されます。後者は多面体セルを記述するために必要なすべての情報を保持できないためです。

---

```
VTKPolyhedron(connectivity, faces...)
```

接続ベクトルから多面体セルを構築します（詳細は[`MeshCell`](@ref)を参照）および多面体の面のリストから構築します。

# 例

8つの点と6つの面を持つ多面体を作成します。8つの点が適切に配置されていれば、これは立方体を表すことができます。

```jldoctest
julia> cell = VTKPolyhedron(
           1:8,
           (1, 4, 3, 2),
           (1, 5, 8, 4),
           (5, 6, 7, 8),
           (6, 2, 3, 7),
           (1, 2, 6, 5),
           (3, 4, 8, 7),
       )
VTKPolyhedron{UnitRange{Int64}, NTuple{6, NTuple{4, Int64}}}(1:8, ((1, 4, 3, 2), (1, 5, 8, 4), (5, 6, 7, 8), (6, 2, 3, 7), (1, 2, 6, 5), (3, 4, 8, 7)))
```
