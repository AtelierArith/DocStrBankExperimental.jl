```
get_point_data(pvtk_file::PVTKFile)
```

指定されたPVTKファイルのポイントデータを持つ`PVTKData`オブジェクトの軽量ベクターを取得します。読み取られるのは数値データ（すなわち`DataArray`）要素のみです。

参照: [`PVTKData`](@ref), [`get_cell_data`](@ref), [`get_field_data`](@ref)
