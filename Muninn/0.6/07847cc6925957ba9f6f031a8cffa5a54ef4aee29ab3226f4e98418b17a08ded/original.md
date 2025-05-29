```
TImodel2(params::Parameters; DDF_snow::F = 3.0/1000.0, DDF_ice::F = 6.0/1000.0, acc_factor::F = 1.0/1000.0) where {F <: AbstractFloat}
```

Create a temperature-index model with two degree-day factors (TImodel2) for mass balance calculations.

# Arguments

  * `params::Parameters`: The parameters object containing simulation settings.
  * `DDF_snow::F`: Degree-day factor for snow (default: 3.0/1000.0).
  * `DDF_ice::F`: Degree-day factor for ice (default: 6.0/1000.0).
  * `acc_factor::F`: Accumulation factor (default: 1.0/1000.0).

# Returns

  * `TI2_model`: An instance of the TImodel2 with the specified parameters.
