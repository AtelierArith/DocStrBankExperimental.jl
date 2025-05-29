```
q_vap_saturation(T, ρ[, q::PhasePartition])
```

Compute the saturation specific humidity, given

  * `T` temperature
  * `ρ` (moist-)air density

and, optionally,

  * `q` [`PhasePartition`](@ref)

If the `PhasePartition` `q` is given, the saturation specific humidity is that of a mixture of liquid and ice, computed in a thermodynamically consistent way from the weighted sum of the latent heats of the respective phase transitions (Pressel et al., JAMES, 2015). That is, the saturation vapor pressure and from it the saturation specific humidity are computed from a weighted mean of the latent heats of vaporization and sublimation, with the weights given by the fractions of condensates `q.liq/(q.liq + q.ice)` and `q.ice/(q.liq + q.ice)` that are liquid and ice, respectively.

If the `PhasePartition` `q` is not given, or has zero liquid and ice specific humidities, the saturation specific humidity is that over a mixture of liquid and ice, with the fraction of liquid given by temperature dependent `liquid_fraction(T)` and the fraction of ice by the complement `1 - liquid_fraction(T)`.
