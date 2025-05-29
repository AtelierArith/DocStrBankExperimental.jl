```
findlead!(panel::PanelStructure, l::Integer=1)
```

Construct a vector of indices of the `l`th lead values for all id-time combinations of `panel` and save the result in `panel.laginds`. If a lead value does not exist, its index is filled with 0. See also [`ilead!`](@ref).
