```
dew_point(Tair,VPD; ...)
dew_point_from_e(ea; ...)
```

Calculate the dew point, the temperature to which air must be               cooled to become saturated (i*e* e = Esat(Td))

# Arguments

  * Tair:     Air temperature (degC)
  * VPD:      Vapor pressure deficit (kPa)
  * ea:       actual water vapor pressure (kPa)

optional

  * accuracy = 1e-03: Accuracy of the result (deg C)
  * `Esat_formula`: formula used in [`Esat_from_Tair`](@ref)
  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries    Pa2kPa

# Details

Dew point temperature (Td) is defined by the temperature for which saturaed vapour pressure equals current vapour pressure, i.e. below which  water would start to condensate.

$e = Esat(Td)$

where e is vapor pressure of the air and Esat is the vapor pressure deficit.          This equation is solved for Td by optimization.

# Value

dew point temperature (degC)

# References

Monteith J.L., Unsworth M.H., 2008: Principles of Environmental Physics.             3rd edition. Academic Press, London.

# Examples

```@example doc
Tair = 20.0
VPD = 1.5
Td = dew_point(Tair, VPD; accuracy = 1e-2)                
(e = VPD_to_e(VPD,Tair), esat_Td = Esat_from_Tair(Td))
```
