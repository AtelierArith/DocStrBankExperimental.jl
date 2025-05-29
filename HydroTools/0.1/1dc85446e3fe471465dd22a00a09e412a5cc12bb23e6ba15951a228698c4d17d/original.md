cal_Rli(Ta, ea=0, s=1, method="MAR")

Estimate Incoming longwave radiation. Not included in FAO56 paper but added for convenience.

# Arguments

  * `Ta`: Near surface air temperature in degrees Celsius.
  * `ea`: Near surface actual vapour pressure in kPa. Default is 0.
  * `s`: Cloud air emissivity, the ratio between actual incoming shortwave radiation and clear sky incoming shortwave radiation. Default is 1.
  * `method`: The method to estimate the air emissivity. Must be one of 'MAR', 'SWI', 'IJ', 'BRU', 'SAT', 'KON'. Default is 'MAR'.

# Returns

  * Incoming longwave radiation in W/m².

# References

1. Satterlund, D. R. (1979), An improved equation for estimating long-wave radiation from the atmosphere, Water Resour. Res., 15( 6), 1649– 1650, doi:10.1029/WR015i006p01649.
2. Sedlar, J., & Hock, R. (2009). Testing longwave radiation parameterizations under clear and overcast skies at Storglaciären, Sweden. The Cryosphere, 3(1), 75-84.
