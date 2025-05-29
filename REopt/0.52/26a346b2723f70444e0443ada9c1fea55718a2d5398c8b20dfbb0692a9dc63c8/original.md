```
MPCScenario(d::Dict)
```

Method for creating the MPCScenario struct:

```julia
    struct MPCScenario <: AbstractScenario
        settings::Settings
        pvs::Array{MPCPV, 1}
        storage::Storage
        electric_tariff::MPCElectricTariff
        electric_load::MPCElectricLoad
        electric_utility::ElectricUtility
        financial::MPCFinancial
        generator::MPCGenerator
        cooling_load::MPCCoolingLoad
        limits::MPCLimits
        node::Int
    end
```

The Dict `d` must have at a minimum the keys:     - "ElectricLoad"     - "ElectricTariff"

Other options include:     - "PV", which can contain a Dict or Dict[]     - "ElectricStorage"     - "Generator"     - "ElectricUtility"     - "Settings"     - "Financial"     - "Limits"
