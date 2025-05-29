```
wind_profile(z::Number, ustar, d, z0m, psi_m = zero(z); constants)
wind_profile(z, df::AbstractDataFrame, d, z0m, psi_m::AbstractVector; constants)
wind_profile(z, df::DFTable, d, z0m; psi_m = nothing,
  stab_formulation = Dyer1970(), constants)
```

Wind speed at a given height above the canopy estimated from single-level measurements of wind speed.

# Arguments

  * `z`         : Height above ground for which wind speed is calculated.
  * `ustar`     : Friction velocity (m s-1)
  * `d`         : Zero-plane displacement height (-)
  * `z0m`       : Roughness length (m)
  * `constants=`[`BigleafConstants`](@ref)`()`

For DataFrame variant with supplying stability_parameter

  * `df`:         : DataFrame with columns 

      * `ustar`     : Friction velocity (m s-1)
  * `psi_m`     : value of the stability function for heat, see [`stability_correction`](@ref) Pass `psi_m = 0.0` to neglect stability correction.

For DataFrame varinat where psi_m is to be estimated

  * additional columns in `df`:

      * `Tair`, `pressure`, `H` : see [`stability_correction`](@ref)

# Details

The underlying assumption is the existence of a logarithmic wind profile above the height d + z0m (the height at which wind speed mathematically reaches zero according to the Monin-Obhukov similarity theory). In this case, the wind speed at a given height z is given by:

$u(z) = (ustar/k) * (ln((z - d) / z0m) - \psi_m$

The roughness parameters zero-plane displacement height (d) and roughness length (z0m) can be approximated from [`roughness_parameters`](@ref).  $\psi_m$ is the stability correction. Set it to zero (not recommended) to neglect statbility correction. By default it is estimated from wind profile using [`stability_correction`](@ref)

# Note

Note that this equation is only valid for z >= d + z0m, and it is not  meaningful to calculate values closely above d + z0m. All values in `heights` smaller than d + z0m will return 0. 

# Value

wind speed at given height `z`. 

# References

  * Monteith, J*L., Unsworth, M*H., 2008: Principles of Environmental Physics. 3rd edition. Academic Press, London.
  * Newman, J*F., Klein, P*M., 2014: The impacts of atmospheric stability on the accuracy of wind speed extrapolation methods. Resources 3, 81-105.

# See also

[`roughness_parameters`](@ref)

```jldoctest; output = false
using DataFrames
heights = 18:2:40  # heights above ground for which to calculate wind speed
df = DataFrame(
  Tair=25.0,pressure=100.0,wind=[3.0,4,5],ustar=[0.5,0.6,0.65],H=[200.0,230,250]) 
zr=40;zh=25;d=16
# z0m and MOL are independent of height, compute before
MOL = Monin_Obukhov_length.(df.Tair, df.pressure, df.ustar, df.H)
z0m = roughness_parameters(
  Roughness_wind_profile(), df.ustar, df.wind, df.Tair, df.pressure, df.H; zh, zr).z0m 
ws = map(heights) do z
  wind_profile(z,df,d,z0m; MOL)
end
using Plots # plot wind profiles for the three rows in df
plot(first.(ws), heights, ylab = "height (m)", xlab = "wind speed (m/s)", legend=:topleft)
plot!(getindex.(ws, 2), heights)
plot!(getindex.(ws, 3), heights)
nothing
# output
```
