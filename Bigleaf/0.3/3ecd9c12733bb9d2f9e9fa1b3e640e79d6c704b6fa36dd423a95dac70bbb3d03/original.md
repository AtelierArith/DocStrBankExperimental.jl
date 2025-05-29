```
LE_to_ET(LE,Tair)
ET_to_LE(ET,Tair)
```

Convert evaporative water flux from mass (ET=evapotranspiration)              to energy (LE=latent heat flux) units, or vice versa.

# Arguments

  * LE   Latent heat flux (W m-2)
  * ET   Evapotranspiration (kg m-2 s-1)
  * Tair Air temperature (deg C)

# Details

The conversions are given by:

  * $ET = LE/\lambda$
  * $LE = \lambda ET$

where $\lambda$ is the latent heat of vaporization (J kg-1) as calculated by [`latent_heat_vaporization`](@ref).

# Examples

```jldoctest; output = false
# LE of 200 Wm-2 and air temperature of 25degC
ET = LE_to_ET(200,25)
≈(ET, 8.19e-5, atol =1e-7)
# output
true
```
