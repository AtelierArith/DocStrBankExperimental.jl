```
StandardBlackOilSystem(; rs_max = nothing,
                         rv_max = nothing,
                         phases = (AqueousPhase(), LiquidPhase(), VaporPhase()),
                         reference_densities = [786.507, 1037.84, 0.969758])
```

Set up a standard black-oil system. Keyword arguments `rs_max` and `rv_max` can either be nothing or callable objects / functions for the maximum Rs and Rv as a function of pressure. `phases` can be specified together with `reference_densities` for each phase.

NOTE: For the black-oil model, the reference densities significantly impact many aspects of the PVT behavior. These should generally be set consistently with the other properties.
