```
MultiSegmentWell(reservoir_cells, volumes, centers;
                N = nothing,
                name = :Well,
                perforation_cells = nothing,
                segment_models = nothing,
                segment_length = nothing,
                reference_depth = 0,
                dz = nothing,
                surface_conditions = default_surface_cond(),
                accumulator_volume = mean(volumes),
                )
```

`reservoir_cells`のベクトルに対応する`volumes`とセル`centers`を持つ井戸を作成します。

# 注意

[`setup_vertical_well`](@ref) または [`setup_well`](@ref) は井戸を設定するための推奨方法です。

# フィールド

  * `type`
  * `volumes`
  * `perforations`
  * `neighborship`
  * `top`
  * `centers`
  * `surface`
  * `name`
  * `segment_models`
  * `material_thermal_conductivity`
  * `material_density`
  * `material_heat_capacity`
  * `void_fraction`
