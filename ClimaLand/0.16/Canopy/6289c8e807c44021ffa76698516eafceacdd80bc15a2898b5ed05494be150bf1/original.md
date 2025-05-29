```
 ClimaLand.make_update_aux(canopy::CanopyModel{FT,
                                              <:AutotrophicRespirationModel,
                                              <:Union{BeerLambertModel, TwoStreamModel},
                                              <:FarquharModel,
                                              <:MedlynConductanceModel,
                                              <:PlantHydraulicsModel,},
                          ) where {FT}
```

Creates the `update_aux!` function for the `CanopyModel`; a specific method for `update_aux!` for the case where the canopy model components are of the type in the parametric type signature: `AutotrophicRespirationModel`, `AbstractRadiationModel`, `FarquharModel`, `MedlynConductanceModel`, and `PlantHydraulicsModel`.

Please note that the plant hydraulics model has auxiliary variables that are updated in its prognostic `compute_exp_tendency!` function. While confusing, this is better for performance as it saves looping over the state vector multiple times.

The other sub-components rely heavily on each other, so the version of the `CanopyModel` with these subcomponents has a single update_aux! function, given here.
