```
Gb_Su(Tair,pressure,ustar; wind_zh, Dl, fc, N=2, Cd=0.2, hs=0.01, constants)
Gb_Su!(df; wind_zh, Dl, fc=nothing, N=2, Cd=0.2, hs=0.01, LAI, constants)
```

Estimate Boundary Layer Conductance to heat transfer using the physically based  formulation according to Su et al. 2001. 

# Arguments

  * `Tair`      : Air temperature (degC)
  * `pressure`  : Atmospheric pressure (kPa)
  * `ustar`     : Friction velocity (m s-1)
  * `df`        : DataFrame or matrix containing the above variables
  * `Dl`        : Leaf characteristic dimension (m)
  * `fc`        : Fractional vegetation cover (0-1), if not provided, calculated from LAI
  * `LAI`       : One-sided leaf area index (-) - alternative to `fc`.
  * `N`         : Number of leaf sides participating in heat exchange (defaults to 2)
  * `Cd`        : Foliage drag coefficient (-)
  * `hs`        : Roughness height of the soil (m)
  * `constants=`[`BigleafConstants`](@ref)`()`

# Value

see [`compute_Gb!`](@ref)

# Details

The formulation is based on the kB^(-1) model developed by Massman 1999.  Su et al. 2001 derived the following approximation:

$k_{B1} = (k C_d f_c^2) / (4C_t u^*/u(z_h)) + k_{Bs-1}(1 - f_c)^2$

If $f_c$ (fractional vegetation cover) is missing, it is estimated from LAI: $f_c = 1 - e^{-LAI/2}$

The wind speed at the top of the canopy is calculated using function [`wind_profile`](@ref).

Ct is the heat transfer coefficient of the leaf (Massman 1999):

$C_t = P_r^{-2/3} R_{eh}^{-1/2}  N$

where $P_r$ is the Prandtl number (set to 0.71),  and $R_{eh}$ is the Reynolds number for leaves:

$R_{eh} = D_l \, wind(z_h) / v$

k*{Bs-1}, the k*{B-1} value for bare soil surface, is calculated according  to Su et al. 2001:

$k_{Bs-1} = 2.46(Re)^{0.25} - ln(7.4)$

# References

  * Su, Z., Schmugge, T., Kustas, W. & Massman, W., 2001: An evaluation of two models for estimation of the roughness height for heat transfer between the land surface and the atmosphere. Journal of Applied Meteorology 40, 1933-1951.
  * Massman, W., 1999: A model study of kB H- 1 for vegetated surfaces using localized near-field' Lagrangian theory. Journal of Hydrology 223, 27-43.
  * Hicks, B*B., Baldocchi, D*D., Meyers, T*P., Hosker, J*R., Matt, D_R., 1987:  A preliminary multiple resistance routine for deriving dry deposition velocities from measured quantities. Water, Air, and Soil Pollution 36, 311-330.

```jldoctest; output = false
using DataFrames
df = DataFrame(
  Tair=25.0,pressure=100.0,wind=[3.0,4,5],ustar=[0.5,0.6,0.65],H=[200.0,230,250])
zh = 25; zr = 40
z0m = roughness_parameters(
  Roughness_wind_profile(), df.ustar, df.wind, df.Tair, df.pressure, df.H; zh, zr).z0m 
wind_zh = wind_profile(zh, df, 0.7*zh, z0m)
compute_Gb!(df,Su2001(); wind_zh, Dl=0.01, LAI=5)
# the same meteorological conditions, but larger leaves
compute_Gb!(df,Su2001(); wind_zh, Dl=0.1,LAI=5)
# same conditions, large leaves, and sparse canopy cover (LAI = 1.5)
compute_Gb!(df,Su2001(); wind_zh, Dl=0.1,LAI=1.5)
≈(df.Gb_h[1], 0.0638, rtol=1e-3)
# output
true
```
