```
Gb_Choudhury(; leafwidth, LAI, wind_zh, constants)
Gb_Choudhury!(df; leafwidth, LAI, wind_zh, constants)
```

Estimate the canopy boundary layer conductance  for heat transfer according to Choudhury & Monteith 1988.

# Arguments

  * `df`               : DataFrame where `Gb_h` is to be added/updated
  * `leafwidth`        : Leaf width (m)
  * `LAI`              : One-sided leaf area index
  * `wind_zh`          : Wind speed at canopy heihgt (m s-1), see [`wind_profile`](@ref)
  * `constants=`[`BigleafConstants`](@ref)`()`

# Value

see [`compute_Gb!`](@ref)

# Details

Boundary layer conductance according to Choudhury & Monteith 1988 is given by:

$Gb_h = LAI \left( 2a/\alpha \sqrt{u(z_h)/w} (1-e^{-\alpha/2})\right)$

where $\alpha$ is modeled as an empirical relation to LAI (McNaughton & van den Hurk 1995):

$\alpha = 4.39 - 3.97 e^{-0.258 \, LAI}$

$w$ is leafwidth and $u(zh)$ is the wind speed at the canopy surface.

It can be approximated from measured wind speed at sensor height zr and a wind extinction  coefficient $\alpha$: $u(z_h) = u(z_r) / e^{\alpha(z_r/z_h -1)}$. However, here (if not explicitly given) it is estimated by [`wind_profile`](@ref)

# References

  * Choudhury, B. J., Monteith J_L., 1988: A four-layer model for the heat budget of homogeneous land surfaces. Q. J. R. Meteorol. Soc. 114, 373-398.
  * McNaughton, K. G., Van den Hurk, B*J*J_M., 1995: A 'Lagrangian' revision of the resistors in the two-layer model for calculating the energy budget of a plant canopy. Boundary-Layer Meteorology 74, 261-288.
  * Hicks, B*B., Baldocchi, D*D., Meyers, T*P., Hosker, J*R., Matt, D_R., 1987: A preliminary multiple resistance routine for deriving dry deposition velocities from measured quantities. Water, Air, and Soil Pollution 36, 311-330.
