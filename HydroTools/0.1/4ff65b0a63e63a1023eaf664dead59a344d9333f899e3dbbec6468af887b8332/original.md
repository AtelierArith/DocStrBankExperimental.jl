cal_Rsi(lat, J, ssd=nothing, cld=nothing, Z=0, a=0.25, b=0.5)

Daily inward shortwave solar radiation at crop surface in W m-2 by providing sunshine duration (SSD) in hours or cloud cover in fraction.

# Arguments

  * `lat`: Latitude in degrees.
  * `J`: Day of the year.
  * `ssd`: Sunshine duration in hours. If `ssd` is `nothing`, `Rsi` is the clear-sky solar radiation. Default is `nothing`.
  * `cld`: Cloud cover in fraction. If provided it would be directly used to calculate solar radiation rather than SSD and parameter a and b. Default is `nothing`.
  * `Z`: Elevation in meters. Default is 0.
  * `a`: Coefficient of the Angstrom formula. Determine the relationship between ssd and radiation. Default is 0.25.
  * `b`: Coefficient of the Angstrom formula. Default is 0.50.

# Returns

  * A tuple of solar radiation at crop surface in W m-2:

      * `Rsi`: Surface downward shortwave radiation.
      * `Rsi_o`: Clear-sky surface downward shortwave radiation.
      * `Rsi_toa`: Extraterrestrial radiation.

# Example

```julia
Rsi, Rsi_o, Rsi_toa = cal_Rsi(lat, J, ssd; Z)
```
