```
AmberFF(
    ::AbstractAtomContainer{T},
    param_file::AbstractString = ball_data_path("forcefields/AMBER/amber96.ini")
)
```

指定された原子コンテナと指定されたパラメータファイル（デフォルト：AMBER96）のためにAMBER力場を初期化します。

# サポートされているキーワード引数

  * `nonbonded_cutoff::T = 20`
  * `vdw_cutoff::T = 15`
  * `vdw_cuton::T = 13`
  * `electrostatic_cutoff::T = 15`
  * `electrostatic_cuton::T = 13`
  * `scaling_vdw_1_4 = 2`
  * `scaling_electrostatic_1_4::T = 1.2`
  * `distance_dependent_dielectric::Bool = false`
  * `assign_charges::Bool = true`
  * `assign_typenames::Bool = true`
  * `assign_types::Bool = true`
  * `overwrite_nonzero_charges::Bool = true`
  * `overwrite_typenames::Bool = false`
  * `periodic_boundary_conditions::Bool = false`
  * `periodic_box_width::T = 100`
  * `periodic_box_height::T = 100`
  * `periodic_box_depth::T = 100`
  * `max_number_of_unassigned_atoms::Int = typemax(Int32)`
