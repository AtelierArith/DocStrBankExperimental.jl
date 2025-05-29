```
Scenario(d::Dict)
```

Scenario構造体のコンストラクタで、`d`は大文字のキーを持ちます：

  * [Site](@ref) (必須)
  * [ElectricTariff](@ref) (必須)
  * [ElectricLoad](@ref) (必須)
  * [PV](@ref) (オプション、配列可)
  * [Wind](@ref) (オプション)
  * [Storage](@ref) (オプション)
  * [ElectricUtility](@ref) (オプション)
  * [Financial](@ref) (オプション)
  * [Generator](@ref) (オプション)
  * [DomesticHotWaterLoad](@ref) (オプション)
  * [SpaceHeatingLoad](@ref) (オプション)
  * [ExistingBoiler](@ref) (オプション)
  * [CHP](@ref) (オプション)

`d`のすべての値は`Dict`であることが期待されますが、`PV`は`Dict`または`Dict[]`のいずれかであることができます。

```
struct Scenario
    settings::Settings
    site::Site
    pvs::Array{PV, 1}
    wind::Wind
    storage::Storage
    electric_tariff::ElectricTariff
    electric_load::ElectricLoad
    electric_utility::ElectricUtility
    financial::Financial
    generator::Generator
    dhw_load::DomesticHotWaterLoad
    space_heating_load::SpaceHeatingLoad
    existing_boiler::ExistingBoiler
    chp::CHP
end
```
