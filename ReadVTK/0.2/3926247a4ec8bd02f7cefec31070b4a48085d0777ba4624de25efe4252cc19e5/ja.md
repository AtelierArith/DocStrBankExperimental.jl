```
get_coordinate_data(vtk_file::VTKFile)
```

指定されたVTKファイルの座標データを持つ軽量の`VTKData`オブジェクトを取得します。数値データ（すなわち、`DataArray`）要素の座標のみが読み取られます。

参照: [`VTKData`](@ref), [`get_point_data`](@ref), [`get_cell_data`](@ref), [`get_field_data`](@ref)
