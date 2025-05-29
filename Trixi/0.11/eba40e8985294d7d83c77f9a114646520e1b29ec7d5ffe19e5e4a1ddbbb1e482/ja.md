```
struct BoundaryConditionNavierStokesWall
```

圧縮性ナビエ-ストークス方程式の壁型境界条件を作成します。詳細は[`CompressibleNavierStokesDiffusion1D`](@ref)、[`CompressibleNavierStokesDiffusion2D`](@ref)、および[`CompressibleNavierStokesDiffusion3D`](@ref)を参照してください。フィールド`boundary_condition_velocity`および`boundary_condition_heat_flux`は、[`NoSlip`](@ref)速度境界条件や[`Adiabatic`](@ref)または[`Isothermal`](@ref)熱境界条件などの境界条件タイプを意図しています。
