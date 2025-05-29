```
calc_effective_rainfall(
    rainfall::Float64, cmd::Float64, d::Float64,
    d2::Float64; n::Float64=0.1
)::Float64
```

Estimate effective rainfall.

# References

  * Croke, B.F.W., Jakeman, A.J. 2004 A catchment moisture deficit module for the IHACRES rainfall-runoff model, Environmental Modelling & Software, 19(1), pp. 1-5. doi: 10.1016/j.envsoft.2003.09.001
  * Croke, B.F.W., Jakeman, A.J. 2005 Corrigendum to "A Catchment Moisture Deficit module for the IHACRES rainfall-runoff model [Environ. Model. Softw. 19 (1) (2004) 1-5]" Environmental Modelling & Software, 20(7), p. 997. doi: https://doi.org/10.1016/j.envsoft.2004.11.004

# Arguments

  * `rainfall`: rainfall for time step
  * `cmd`: previous CMD value
  * `d`: threshold value
  * `d2`: scaling factor applied to `d`
  * `n`: scaling factor (default = 0.1). Default value is suitable for most cases (Croke & Jakeman, 2004)

# Returns

  * Effective rainfall value
