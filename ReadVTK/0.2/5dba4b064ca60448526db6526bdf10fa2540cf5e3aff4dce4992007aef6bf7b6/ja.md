```
get_coordinates(vtk_file::VTKFile; x_string="x", y_string="y", z_string="z")
```

RectilinearGridファイルの各方向のVTK座標ベクトルを1Dベクトルのタプルとして取得します。

VTKでは、ポイントは常に三次元で保存されるため、1Dまたは2Dファイルの場合でも、常に3つのベクトルを持つタプルが取得されます。

参照: [`get_cells`](@ref)
