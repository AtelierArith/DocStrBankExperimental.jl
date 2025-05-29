```
MPCScenario(d::Dict)
```

Method for creating the MPCScenario struct:     struct MPCScenario <: AbstractScenario         settings::Settings         pvs::Array{MPCPV, 1}         storage::MPCStorage         electric*tariff::MPCElectricTariff         electric*load::MPCElectricLoad         electric_utility::ElectricUtility         financial::MPCFinancial         generator::MPCGenerator     end The Dict `d` must have at a minimum the keys:     - "ElectricLoad"     - "ElectricTariff" Other options include:     - "PV", which can contain a Dict or Dict[]     - "Storage"     - "Generator"     - "ElectricUtility"     - "Settings"     - "Financial"
