```
create_node(m, n::Availability, 𝒯, 𝒫, modeltype::EnergyModel)
```

Set all constraints for a `Availability`. Can serve as fallback option for all unspecified subtypes of `Availability`.

`Availability` nodes can be seen as routing nodes. It is not necessary to have more than one available node except if one wants to include as well transport between different `Availability` nodes with associated costs (not implemented at the moment).
