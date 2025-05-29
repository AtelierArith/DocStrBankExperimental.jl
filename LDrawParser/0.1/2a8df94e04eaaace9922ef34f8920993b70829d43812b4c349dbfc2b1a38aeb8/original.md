```
change_coordinate_system!(model::MPDModel, T=ldraw_base_transform(), scale=1.0; ignore_rotation_determinant=false)
```

Transform the coordinate system of the entire model using transform `T` and scale `scale`.
