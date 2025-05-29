```
ImmersedBoundaryGrid(grid, ib::AbstractImmersedBoundary;
                     active_cells_map=false, active_z_columns=active_cells_map)
```

`AbstractImmersedBoundary`が埋め込まれた境界（`ib`）を持つグリッドを返します。`active_cells_map`または`active_z_columns`が`true`の場合、グリッドは`interior_active_cells`および`active_z_columns`フィールドを埋めます。これは、それぞれ内部のアクティブインデックスのリストと、縮小されたx-y平面上のアクティブインデックスのリストです。
