```
Scenario(d::Dict; flex_hvac_from_json=false)
```

A Scenario struct can contain the following keys:

  * [Site](@ref) (required)
  * [Financial](@ref) (optional)
  * [ElectricTariff](@ref) (required when `off_grid_flag=false`)
  * [ElectricLoad](@ref) (required)
  * [PV](@ref) (optional, can be Array)
  * [Wind](@ref) (optional)
  * [ElectricStorage](@ref) (optional)
  * [HotThermalStorage](@ref) (optional)
  * [ColdThermalStorage](@ref) (optional)
  * [ElectricStorage](@ref) (optional)
  * [ElectricUtility](@ref) (optional)
  * [Generator](@ref) (optional)
  * [HeatingLoad](@ref) (optional)
  * [CoolingLoad](@ref) (optional)
  * [ExistingBoiler](@ref) (optional)
  * [Boiler](@ref) (optional)
  * [CHP](@ref) (optional)
  * [FlexibleHVAC](@ref) (optional)
  * [ExistingChiller](@ref) (optional)
  * [AbsorptionChiller](@ref) (optional)
  * [GHP](@ref) (optional, can be Array)
  * [SteamTurbine](@ref) (optional)
  * [ElectricHeater](@ref) (optional)
  * [ASHP](@ref) (optional)

All values of `d` are expected to be `Dicts` except for `PV` and `GHP`, which can be either a `Dict` or `Dict[]` (for multiple PV arrays or GHP options).

!!! note
    Set `flex_hvac_from_json=true` if `FlexibleHVAC` values were loaded in from JSON (necessary to  handle conversion of Vector of Vectors from JSON to a Matrix in Julia).

