```
pressure_from_elevation(elev,Tair,VPD=missing;...)
```

An estimate of mean pressure at a given elevation as predicted by the              hypsometric equation.

# Arguments

  * elev:      Elevation a*s*l_ (m)
  * Tair:      Air temperature (deg C)
  * VPD:       Vapor pressure deficit (kPa); optional

optional 

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries    Kelvin, pressure0, Rd, g, Pa2kPa

# Details

Atmospheric pressure is approximated by the hypsometric equation:

$pressure = pressure_0 / (exp(g * elevation / (Rd Temp)))$

The hypsometric equation gives an estimate of the standard pressure       at a given altitude.       If VPD is provided, humidity correction is applied and the       virtual temperature instead of air temperature is used_ VPD is        internally converted to specific humidity.

# Value

Atmospheric pressure (kPa)

# References

Stull B_, 1988: An Introduction to Boundary Layer Meteorology.             Kluwer Academic Publishers, Dordrecht, Netherlands.

# Examples

```@example doc
# mean pressure at 500m altitude at 25 deg C and VPD of 1 kPa
pressure_from_elevation(500,25,1)
```
