```
Scenario(d::Dict; flex_hvac_from_json=false)
```

Scenario構造体は、以下のキーを含むことができます：

  * [Site](@ref) (必須)
  * [Financial](@ref) (オプション)
  * [ElectricTariff](@ref) (必須、`off_grid_flag=false` の場合)
  * [ElectricLoad](@ref) (必須)
  * [PV](@ref) (オプション、配列可)
  * [Wind](@ref) (オプション)
  * [ElectricStorage](@ref) (オプション)
  * [HotThermalStorage](@ref) (オプション)
  * [ColdThermalStorage](@ref) (オプション)
  * [ElectricStorage](@ref) (オプション)
  * [ElectricUtility](@ref) (オプション)
  * [Generator](@ref) (オプション)
  * [HeatingLoad](@ref) (オプション)
  * [CoolingLoad](@ref) (オプション)
  * [ExistingBoiler](@ref) (オプション)
  * [Boiler](@ref) (オプション)
  * [CHP](@ref) (オプション)
  * [FlexibleHVAC](@ref) (オプション)
  * [ExistingChiller](@ref) (オプション)
  * [AbsorptionChiller](@ref) (オプション)
  * [GHP](@ref) (オプション、配列可)
  * [SteamTurbine](@ref) (オプション)
  * [ElectricHeater](@ref) (オプション)
  * [ASHP](@ref) (オプション)

`d`のすべての値は`Dict`であることが期待されますが、`PV`と`GHP`は`Dict`または`Dict[]`（複数のPV配列またはGHPオプション用）であることができます。

!!! note
    `FlexibleHVAC`の値がJSONから読み込まれた場合は、`flex_hvac_from_json=true`に設定してください（これは、JSONからJuliaの行列へのベクトルの変換を処理するために必要です）。

