```
ovf2vtk(ovf_name, vtk_name=nothing; point_data=false, box=noting)
```

ovfファイルをvtk形式に変換します。データはpoint_data == trueの場合はポイントに保存され、それ以外の場合はセルに保存されます。

boxがnotingでない場合、それはタプルである必要があります。例えば、box = (nx1, nx2, ny1, ny2, nz1, nz2)のようになります。この場合、生成されるvtkはボックス内（境界を含む）のスピンのみを含みます。

```julia
    ovf2vtk("my.ovf", "test.vts")
    ovf2vtk("my.ovf", point_data=true)
```
