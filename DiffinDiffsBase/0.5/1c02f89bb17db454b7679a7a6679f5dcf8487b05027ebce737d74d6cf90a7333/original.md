```
findlag!(panel::PanelStructure, l::Integer=1)
```

Construct a vector of indices of the `l`th lagged values for all id-time combinations of `panel` and save the result in `panel.laginds`. If a lagged value does not exist, its index is filled with 0. See also [`ilag!`](@ref).
