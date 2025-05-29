```
cal_Rnl(Tmax, Tmin, ea, cld)
cal_Rnl(Tmax, Tmin, ea, Rsi, Rsi_o)
```

Net outgoing longwave radiation.

# Arguments

  * `Tmax`: Daily maximum air temperature at 2m height in degrees Celsius.
  * `Tmin`: Daily minimum air temperature at 2m height in degrees Celsius.
  * `ea`: Actual vapor pressure in kPa. Can be estimated by maximum or minimum air temperature and mean relative humidity.
  * `Rsi`: Incoming shortwave radiation at crop surface in MJ m-2 day-1. Default is `nothing`.
  * `Rsi_o`: Clear sky incoming shortwave radiation, i.e., extraterrestrial radiation multiply by clear sky transmissivity (i.e., a + b, a and b are coefficients of Angstrom formula. Normally 0.75) in MJ m-2 day-1. Default is `nothing`.
  * `cld`: Cloud cover in fraction. If provided it would be directly used to calculate net outgoing longwave radiation than Rso. Default is `nothing`.

# Returns

  * Net outgoing longwave radiation in `W m-2`.
