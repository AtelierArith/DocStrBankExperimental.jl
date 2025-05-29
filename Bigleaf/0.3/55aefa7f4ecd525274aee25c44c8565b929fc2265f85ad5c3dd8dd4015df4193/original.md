```
Esat_slope(Tair; Esat_formula, constants) 
Esat_from_Tair(Tair; Esat_formula, constants) 
Esat_from_Tair_deriv(Tair; Esat_formula, constants)
```

Saturation Vapor Pressure (Esat) and Slope of the Esat Curve

# Arguments

  * `Tair`:      Air temperature (deg C)
  * `Esat_formula=Sonntag1990()`:   Esat_formula to be used. Either   `Sonntag1990()` (Default), `Alduchov1996()`, or `Allen1998()`.
  * `constants=BigleafConstants()`: Dictionary with entry  :Pa2kPa

# Details

Esat (kPa) is calculated using the Magnus equation:

`Esat = a * exp((b * Tair) / (c + Tair)) / 1000` where the coefficients a, b, c take different values depending on the Esat_formula use The default values are from Sonntag 1990 (a=611.2, b=17.62, c=243.12). This versi of the Magnus equation is recommended by the WMO (WMO 2008; p1.4-29). Alternativel parameter values determined by Alduchov & Eskridge 1996 or Allen et al. 1998 can b used (see references). The slope of the Esat curve ($\Delta$) is calculated as the first derivative of the function:

$\Delta = {dEsat \over dTair}$

# Value

  * `Esat_from_Tair`: Saturation vapor pressure (kPa)
  * `Esat_from_Tair_deriv`: Slope of the saturation vapor pressure curve (kPa K-1)
  * `Esat_slope`: A tuple of the two above values

# References

Sonntag D. 1990: Important new values of the physical constants of 1986, vapor  pressure formulations based on the ITS-90 and psychrometric formulae.  Zeitschrift fuer Meteorologie 70, 340-344.

World Meteorological Organization 2008: Guide to Meteorological Instruments and Methods of Observation (WMO-No.8). World Meteorological Organization, Geneva. 7th Edition,

Alduchov, O. A. & Eskridge, R. E., 1996: Improved Magnus form approximation of  saturation vapor pressure. Journal of Applied Meteorology, 35, 601-609

Allen, R.G., Pereira, L.S., Raes, D., Smith, M., 1998: Crop evapotranspiration - Guidelines for computing crop water requirements - FAO irrigation and drainage paper 56, FAO, Rome.

```@example
Esat_from_Tair(20.0)          # Esat in kPa
Esat_from_Tair_deriv(20.0)    # its derivative to temperature in kPa K-1
Esat_slope(20.0)              # both as a tuple
```
