```
constraints_level_aux(m, n::Storage, 𝒯, 𝒫, modeltype::EnergyModel)
constraints_level_aux(m, n::RefStorage{AccumulatingEmissions}, 𝒯, 𝒫, modeltype::EnergyModel)
```

Function for creating the Δ constraint for the level of a generic `Storage` node. `EnergyModelsBase` provides as well a method for a `RefStorage{AccumulatingEmissions}`.
