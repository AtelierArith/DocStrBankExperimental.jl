```
wetbulb_temp(Tair, pressure, VPD; ...)
```

Calculate the wet bulb temperature, i*e* the temperature              that the air would have if it was saturated

# Arguments

  * Tair:      Air temperature (deg C)
  * pressure:  Atmospheric pressure (kPa)
  * VPD:       Vapor pressure deficit (kPa)

optional

  * accuracy:  Accuracy of the result (deg C)
  * `Esat_formula`: formula used in [`Esat_from_Tair`](@ref)
  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries     cp, eps,Pa2kPa

# Details

Wet-bulb temperature (Tw) is calculated from the following expression:

$e = Esat(Tw) - gamma* (Tair - Tw)$

The equation is optimized for Tw. Actual vapor pressure e (kPa) is calculated from VPD using [`VPD_to_e`](@ref). The psychrometric constant gamma (kPa K-1) is calculated using [`psychrometric_constant`](@ref).

# Value

wet-bulb temperature (degC)

# References

Monteith J.L., Unsworth M.H., 2008: Principles of Environmental Physics.             3rd edition. Academic Press, London.

# Examples

```@example doc
wetbulb_temp.([20,25.0], 100, [1,1.6])             
```
