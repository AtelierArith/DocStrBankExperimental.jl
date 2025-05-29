```
capacity_from_wind(v::Real; TSP::Real, Cp=0.50, v_out=25.0, α=3.0)
```

Compute capacity factor (normalized power) of a wind turbine, using a generic parametrized power curve P(v), for a given a wind speed `v` (m/s).

Model parameters are:

  * Turbine Specific Power `TSP`, in W/m², typically 200 – 400.
  * Maximum power coefficient `Cp` (used before saturation) should be smaller than Betz' limit of 16/27.
  * Cut-out wind speed is `v_out` (m/s).

A fixed Cp model is used, with a soft saturation when reaching maximum power. This soft saturation, based on LogSumExp, is tuned with `α` (default: 3.0, higher yields sharper transition).

Air is assumed to have fixed density ρ=1.225 kg/m³.
