```
 convertTECtoVTU(file::AbstractString, outname="out")
 convertTECtoVTU(head, data, connectivity, outname="out")
```

非構造化TecplotデータをVTKに変換します。VTKでボクセルタイプのデータを使用する場合、接続順序がTecplotとは異なることに注意してください：Tecplotの3D接続順序はVTKの`hexahedron`タイプと同じですが、`voxel`タイプとは異なります。2D接続順序は`quad`タイプと同じですが、`pixel`タイプとは異なります。例えば、3Dでのインデックス変換は次のようになります：

```
# PLT to VTK voxel index_ = [1 2 4 3 5 6 8 7]
for i in 1:2
	connectivity = swaprows!(connectivity, 4*i-1, 4*i)
end
```
