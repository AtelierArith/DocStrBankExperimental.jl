```
MPCScenario(d::Dict)
```

MPCScenario構造体を作成するためのメソッド:     struct MPCScenario <: AbstractScenario         settings::Settings         pvs::Array{MPCPV, 1}         storage::MPCStorage         electric*tariff::MPCElectricTariff         electric*load::MPCElectricLoad         electric_utility::ElectricUtility         financial::MPCFinancial         generator::MPCGenerator     end Dict `d` には最低限次のキーが必要です:     - "ElectricLoad"     - "ElectricTariff" その他のオプションには次が含まれます:     - "PV"（DictまたはDict[]を含むことができます）     - "Storage"     - "Generator"     - "ElectricUtility"     - "Settings"     - "Financial"
