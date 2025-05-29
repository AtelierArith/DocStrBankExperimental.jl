```
change_coordinate_system!(model::MPDModel, T=ldraw_base_transform(), scale=1.0; ignore_rotation_determinant=false)
```

モデル全体の座標系を変換 `T` を使用して、スケール `scale` で変換します。
