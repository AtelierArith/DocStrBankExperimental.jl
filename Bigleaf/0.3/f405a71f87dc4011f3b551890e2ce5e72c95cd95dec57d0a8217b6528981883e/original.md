```
Monin_Obukhov_length(Tair, pressure, ustar, H; constants)
Monin_Obukhov_length!(df;constants=BigleafConstants())
Monin_Obukhov_length(df;constants=BigleafConstants())
```

calculates the Monin-Obukhov length.

# Arguments

  * `Tair`      : Air temperature (degC)
  * `pressure`  : Atmospheric pressure (kPa)
  * `ustar`     : Friction velocity (m s-1)
  * `H`         : Sensible heat flux (W m-2)
  * `df`        : DataFrame containing the above variables

optional

  * `constants=`[`BigleafConstants`](@ref)`()`: Dictionary with entries 

      * `Kelvin` - conversion degree Celsius to Kelvin
      * `cp` - specific heat of air for constant pressure (J K-1 1)
      * `k` - von Karman constant (-)
      * `g` - gravitational acceleration (m s-2)

# Details

The Monin-Obukhov length (L) is given by:

$L = - (\rho * cp * ustar^3 * Tair) / (k * g * H)$

where $\rho$ is air density (kg m-3).

# Note

Note that L gets very small for very low ustar values with implications for subsequent functions using L as input. It is recommended to filter data and exclude low ustar values (ustar < ~0.2) beforehand. 

# Value

Monin-Obukhov length L (m). The non-mutating DataFrame variant returns a vector, the mutating variant add or modifies column `:MOL`.

# References

Foken, T, 2008: Micrometeorology. Springer, Berlin, Germany. 

# See also

[`stability_parameter`](@ref)

```@example; output = false
Monin_Obukhov_length(
  Tair=25,pressure=100,
  ustar=seq(0.2,1,0.1),H=seq(40,200,20))
```
