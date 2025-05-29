Temperature flux longwave radiation from Jeevanjee and Romps, 2018, following Seeley and Wordsworth, 2023, eq (1)

```
dF/dT = α*(T_t - T)
```

with `F` the upward temperature flux between two layers with temperature difference `dT`, `α = 0.025 W/m²/K²` and `T_t = 200K` a prescribed tropopause temperature. Flux into the lowermost layer is 0. Flux out of uppermost layer also 0, but `dT/dt = (T_t - T)/τ` is added to relax the uppermost layer towards the tropopause temperature `T_t` with time scale `τ = 24h` (Seeley and Wordsworth, 2023 use 6h, which is unstable a low resolutions here). Fields are

  * `α::Any`: Radiative forcing constant (W/m²/K²)
  * `temp_tropopause::Any`: Tropopause temperature [K]
  * `time_scale::Dates.Second`: Tropopause relaxation time scale to temp_tropopause
