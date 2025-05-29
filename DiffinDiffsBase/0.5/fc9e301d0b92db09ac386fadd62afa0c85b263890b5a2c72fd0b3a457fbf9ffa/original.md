```
ilag!(panel::PanelStructure, l::Integer=1)
```

Return a vector of indices of the `l`th lagged values for all id-time combinations of `panel`. The indices are retrieved from `panel` if they have been collected before. Otherwise, they are created by calling [`findlag!`](@ref). See also [`ilead!`](@ref).
