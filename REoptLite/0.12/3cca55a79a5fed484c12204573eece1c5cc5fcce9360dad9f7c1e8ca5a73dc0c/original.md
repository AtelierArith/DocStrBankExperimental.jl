```
Scenario(d::Dict)
```

Constructor for Scenario struct, where `d` has upper-case keys:

  * [Site](@ref) (required)
  * [ElectricTariff](@ref) (required)
  * [ElectricLoad](@ref) (required)
  * [PV](@ref) (optional, can be Array)
  * [Wind](@ref) (optional)
  * [Storage](@ref) (optional)
  * [ElectricUtility](@ref) (optional)
  * [Financial](@ref) (optional)
  * [Generator](@ref) (optional)
  * [DomesticHotWaterLoad](@ref) (optional)
  * [SpaceHeatingLoad](@ref) (optional)
  * [ExistingBoiler](@ref) (optional)
  * [CHP](@ref) (optional)

All values of `d` are expected to be `Dicts` except for `PV`, which can be either a `Dict` or `Dict[]`.

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
