```
remakeSPAC(discrSPAC::DiscretizedSPAC;
            requested_tspan = nothing,
            soil_output_depths_m::Vector = zeros(Float64, 0),
            kwargs...)
```

or

```
remakeSPAC(parametrizedSPAC::SPAC;
            requested_tspan = nothing,
            soil_output_depths_m::Vector = zeros(Float64, 0),
            kwargs...)
```

Generates a copy of the provided SPAC or DiscretizedSPAC and modifies all the parameter that are provided as kwargs. This is useful running the same model with a range of different parameter.

Possible kwargs are:

  * `soil_horizons = (ths_ = 0.4, Ksat_mmday = 3854.9, alpha_per_m = 7.11, gravel_volFrac = 0.1)`
  * `LAI_rel = (DOY_Bstart = 115,)`
  * `root_distribution = (beta = 0.88, z_rootMax_m = -0.6,)`
  * `params = (DRAIN=.33, BYPAR=1, IDEPTH_m=0.67, INFEXP=0.33,           ALB=0.15, ALBSN=0.7, RSSA=720., PSICR=-1.6, FXYLEM=0.4, MXKPL=16.5, MAXLAI=9.999,           GLMAX=.00801, R5=235., CVPD=1.9, CINTRL=0.18,)`
  * `IC_soil = (PSIM_init_kPa = -3.0, delta18O_init_permil = -15.55, )`
  * `IC_scalar = ICscalar_tochange`

When the argument `soil_horizons` contains scalar values, the parameter of the toplayer are set to this value and parameter of all other layers are modified proportionally. Alternatively, the argument `soil_horizons` can be provided with a vector or vectors with a value for each soil horizon. A mix of vectors and scalars is also possible.
