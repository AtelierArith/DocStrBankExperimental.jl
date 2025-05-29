```
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::Data)
```

Fallback option when data is specified, but it is not desired to add the constraints through this function. This is, *e.g.*, the case for `EnergyModelsInvestments` as the capacity constraint has to be replaced.
