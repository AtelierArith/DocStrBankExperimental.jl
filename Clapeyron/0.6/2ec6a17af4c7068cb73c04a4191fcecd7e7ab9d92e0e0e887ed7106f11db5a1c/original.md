```
ClapeyronSaturation <: SaturationMethod
ClapeyronSaturation(T0 = nothing, crit = nothing, satmethod = ChemPotVSaturation())
```

Saturation method for `saturation_temperature`. It solves iteratively `saturation_temperature(model,Ti,satmethod)` until convergence, by using the Clapeyron equation:

```
dp/dT = ΔS/ΔV
```

It descends from the critical point (or `T0`, if provided). Reliable, but slow.

It is recommended that `T0 > Tsat`, as the temperature decrease iteration series is more stable. Default method for `saturation_temperature` until Clapeyron 0.3.7
