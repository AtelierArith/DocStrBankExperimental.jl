```
boundary_var_types(
    ::EnergyHydrology{FT},
    ::AtmosDrivenFluxBC{<:CoupledAtmosphere, <:CoupledRadiativeFluxes},
    ::ClimaLand.TopBoundary,
) where {FT}
```

AtmosDrivenFluxBCの`boundary_var_types`メソッドの拡張で、結合大気と放射フラックスを持っています。これは追加変数の型を指定します。

このメソッドには、大気に必要な追加フラックスが含まれています：運動量フラックス（`ρτxz`、`ρτyz`）と浮力フラックス（`buoy_flux`）。これらは、カプラーが乱流フラックスを計算する際に、その場で更新され、`soil_boundary_fluxes!`では更新されません。

現在、これらは陸地モデルに保存されています。なぜなら、カプラーがClimaLand関数を使用して乱流の陸地/大気フラックスを計算するため、陸地モデルはフラックスを中間的に保存できる必要があるからです。フラックスを完全にカプラー内で計算できるようになれば、これを削除できます。
