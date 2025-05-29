```
cal_Rln_yang2019(Tₛ, Rsi, Rsi_toa; lat=30, ϵ::Float64=0.96, n1=2.52, n2=2.37, n3=0.035)
```

Calculate the longwave radiation based on the Yang et al. (2019) method.

# Arguments

  * `Ts`: Land surface temperature.
  * `Rsi`: Surface incoming short-wave radiation.
  * `Rsi_toa`: Incoming short-wave radiation at the top of the atmosphere.
  * `lat`: Latitude (in degrees). Default is 30.
  * `ϵ`: Emissivity. Default is 0.96.
  * `n1`, `n2`, `n3`: Parameters for `ΔT`. See Yang 2019 for details.

# References

1. Yang, Y., & Roderick, M. L. (2019). Radiation, surface temperature and evaporation over wet surfaces. Quarterly Journal of the Royal Meteorological Society, 145(720), 1118–1129. https://doi.org/10.1002/qj.3481
2. Tu, Z., & Yang, Y. (2022). On the Estimation of Potential Evaporation Under Wet and Dry Conditions. Water Resources Research, 58(4). https://doi.org/10.1029/2021wr031486
