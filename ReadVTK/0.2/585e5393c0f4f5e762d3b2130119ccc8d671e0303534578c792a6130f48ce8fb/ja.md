```
get_point_data(vtk_file::VTKFile)
```

指定されたVTKファイルのポイントデータを持つ軽量の`VTKData`オブジェクトを取得します。数値データ（すなわち、`DataArray`）要素のみが読み込まれます。

参照: [`VTKData`](@ref), [`get_cell_data`](@ref), [`get_field_data`](@ref)
