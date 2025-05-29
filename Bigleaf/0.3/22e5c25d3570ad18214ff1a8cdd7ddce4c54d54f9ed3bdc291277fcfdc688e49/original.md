```
virtual_temp(Tair,pressure,VPD; ...)
```

Virtual temperature, defined as the temperature at which dry air would have the same              density as moist air at its actual temperature.

# Arguments

  * `Tair`:      Air temperature (deg C)
  * `pressure`:  Atmospheric pressure (kPa)
  * `VPD`:       Vapor pressure deficit (kPa)
  * `Esat_formula`: formula used in [`Esat_from_Tair`](@ref)

optional 

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries 

      * :Kelvin - conversion degree Celsius to Kelvin
      * :eps - ratio of the molecular weight of water vapor to dry air (-)

# Details

The virtual temperature is given by:

`Tv = Tair / (1 - (1 - eps) e/pressure)`

where Tair is in Kelvin (converted internally)_ Likewise, VPD is converted   to actual vapor pressure (e in kPa) with [`VPD_to_e`](@ref) internally.

# Value

virtual temperature (deg C)

# References

  * Monteith J.L., Unsworth M.H., 2008: Principles of Environmental Physics.           3rd edition. Academic Press, London.

# Examples

```jldoctest; output = false
Tair,pressure,VPD = 25.0,100.0,1.5
vt = virtual_temp(Tair,pressure,VPD)  
≈(vt, 26.9, atol =0.1)
# output
true
```
