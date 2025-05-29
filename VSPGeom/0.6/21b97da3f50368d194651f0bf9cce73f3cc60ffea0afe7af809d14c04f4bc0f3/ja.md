```
getVTKElements(mesh::TriMesh)
```

VTKファイルに書き込むために必要なデータ構造 `points` と `cells` を返す便利な関数です。ユーザーは次のようにしてVTKファイルを書き出すことができます。

```
WriteVTK.vtk_grid(filename, points, cells) do vtk
end
```

**引数**

  * `mesh::TriMesh`: [`TriMesh`](@ref) オブジェクト

**戻り値**

  * `points::Array{Float64}`: STLメッシュの座標の配列
  * `mesh::Array{meshCell}`: WriteVTKが使用するMeshCellオブジェクトの配列
