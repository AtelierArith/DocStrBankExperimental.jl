```
adiabat_dry_T(P0::FT, Tk0::FT, P::FT, w=nothing)
adiabat_dry_P(P0::FT, Tk0::FT, T::FT, w=nothing)

LCL(T0::FT, Td::FT)
LCL_bolton(T0::FT, Td::FT)

theta(p::FT, tk::FT; p0=1000)
theta_se(p, tk, w=0; p0=1000)

theta_wet(P0, T0, Td)
theta_wet_bolton(P0, T0, Td)
```

# Functions

  * `LCL`       : Bolton 1980, Eq. 15
  * `LCL_bolton`: Bolton 1980, Eq. 22

# Arguments

  * p: surface pressure, hPa
  * Tk0, tk: surface temperature, K
  * T0: surface temperature, degC
  * P0: surface pressure, hPa
  * Td: dew temperature, degC

# References

1. https://unidata.github.io/MetPy/latest/api/generated/metpy.calc.equivalent*potential*temperature.html
2. https://github.com/wrf-model/WRF/blob/master/phys/module*diag*functions.F#L122
3. https://github.com/Unidata/MetPy/blob/e0e24d51702787943fc3c0481fa9a6632abe9d20/src/metpy/calc/thermo.py#L1512

# Examples

```julia
T1 = adiabat_dry_T(850., 20 + K0, 1000.) - K0
P1 = adiabat_dry_P(850., 20 +K0, T1+K0)

theta(850., 20.0 +K0)
theta_se(850., 20.0 +K0)

theta_wet(850., 20.0, 18.0)
theta_wet_bolton(850., 20.0, 18.0)
```
