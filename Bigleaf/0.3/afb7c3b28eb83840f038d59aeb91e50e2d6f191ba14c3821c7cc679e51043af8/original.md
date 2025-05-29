```
BigleafConstants(;...)
```

Constants used throughout the Bigleaf.jl Package

Default values can be overridden by the named arguments of the constructor:

  * cp           : Specific heat of air for constant pressure (J K-1 kg-1)
  * Rgas         : Universal gas constant (J mol-1 K-1)
  * Rv           : Gas constant of water vapor (J kg-1 K-1) (Stull 1988 p.641)
  * Rd           : Gas constant of dry air (J kg-1 K-1) (Foken p. 245)
  * Md           : Molar mass of dry air (kg mol-1)
  * Mw           : Molar mass of water vapor (kg mol-1)
  * eps          : Ratio of the molecular weight of water vapor to dry air (=Mw/Md)
  * g            : Gravitational acceleration (m s-2)
  * solar_constant: Solar constant (W m-2)
  * pressure0    : Reference atmospheric pressure at sea level (Pa)
  * Tair0        : Reference air temperature (K)
  * k            : von Karman constant
  * Cmol         : Molar mass of carbon (kg mol-1)
  * Omol         : Molar mass of oxygen (kg mol-1)
  * H2Omol       : Molar mass of water (kg mol-1)
  * sigma        : Stefan-Boltzmann constant (W m-2 K-4)
  * Pr           : Prandtl number
  * Sc_CO2       : Schmidt number for CO2
  * Kelvin       : Conversion degree Celsius to Kelvin
  * DwDc         : Ratio of the molecular diffusivities for water vapor and CO2
  * days2seconds : Seconds per day
  * kPa2Pa       : Conversion kilopascal (kPa) to pascal (Pa)
  * Pa2kPa       : Conversion pascal (Pa) to kilopascal (kPa)
  * umol2mol     : Conversion micromole (umol) to mole (mol)
  * mol2umol     : Conversion mole (mol) to micromole (umol)
  * kg2g         : Conversion kilogram (kg) to gram (g)
  * g2kg         : Conversion gram (g) to kilogram (kg)
  * kJ2J         : Conversion kilojoule (kJ) to joule (J)
  * J2kJ         : Conversion joule (J) to kilojoule (kJ)
  * se*median    : Conversion standard error (SE) of the mean to SE of the median (http://influentialpoints.com/Training/standard*error*of*median.htm)
  * frac2percent : Conversion between fraction and percent

## Examples

```jldoctest; output=false
BigleafConstants().g == 9.81
# on the moon change gravity constant to 1/6 that of the earth
BigleafConstants(g = BigleafConstants().g/6).g == 9.81/6
# output
true
```
