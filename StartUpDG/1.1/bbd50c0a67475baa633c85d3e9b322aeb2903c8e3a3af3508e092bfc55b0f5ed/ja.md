```
read_Gmsh_2D(filename, args...)
```

2D三角形Gmshファイルを読み込みます。メッシュフォーマット2.2および4.1がサポートされています。 (VX, VY), EToVを返します。

# 例

```julia
VXY, EToV = read_Gmsh_2D("eulerSquareCylinder2D.msh") # v2.2ファイルフォーマット
VXY, EToV = read_Gmsh_2D("test/testset_Gmsh_meshes/periodicity_mesh_v4.msh") # v4.1ファイルフォーマット

# MeshImportOptions.grouping=trueの場合、3つ目の変数`grouping`が返されます
VXY, EToV, grouping = read_Gmsh_2D("test/testset_Gmsh_meshes/periodicity_mesh_v4.msh", MeshImportOptions(true, false))
VXY, EToV, grouping = read_Gmsh_2D("test/testset_Gmsh_meshes/periodicity_mesh_v4.msh", true) # 上と同じ
```

# 参照

https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format-version-2-*0028Legacy*0029
