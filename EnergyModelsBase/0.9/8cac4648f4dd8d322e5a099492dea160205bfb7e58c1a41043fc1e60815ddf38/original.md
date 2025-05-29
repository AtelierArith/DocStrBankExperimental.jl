```
constraints_level(m, n::Storage, 𝒯, 𝒫, modeltype::EnergyModel)
```

Function for creating the level constraints of a `Storage` node. If you create a new `Storage` node, you should include this function in your calls. It provides all information required for the various [`StorageBehavior`](@ref)s.
