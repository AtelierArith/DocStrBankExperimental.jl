```
MPCScenario(d::Dict)
```

MPCScenario構造体を作成するためのメソッド：

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

Dict `d` には最低限次のキーが必要です：     - "ElectricLoad"     - "ElectricTariff"

その他のオプションには次が含まれます：     - "PV"（DictまたはDict[]を含むことができます）     - "ElectricStorage"     - "Generator"     - "ElectricUtility"     - "Settings"     - "Financial"     - "Limits"
