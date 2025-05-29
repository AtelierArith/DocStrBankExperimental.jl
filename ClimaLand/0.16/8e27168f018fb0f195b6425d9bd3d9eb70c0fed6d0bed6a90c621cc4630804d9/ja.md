```
make_update_boundary_fluxes(
    land::LandHydrology{FT, SM, SW},
) where {FT, SM <: Soil.RichardsModel{FT}, SW <: Pond.PondModel{FT}}
```

関数を作成するメソッド; 返される関数は、土壌モデルの境界条件と表面水モデルのソース項（流出）に必要な補助変数 `p.soil_infiltration` を更新します。

この関数は、各ODE関数評価の際に呼び出されます。
