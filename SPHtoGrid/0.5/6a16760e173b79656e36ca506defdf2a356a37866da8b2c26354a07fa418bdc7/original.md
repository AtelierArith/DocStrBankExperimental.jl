```
jγ_PE04(rho_cgs::Real, T_K::Real, α_p::Real, Eγ::Real; 
        Xcr::Real=0.5, xH::Real=0.752)
```

Gamma-ray emissivity at photon energy `Eγ` [GeV] for thermal gas with properties `rho_cgs` [g/cm^3] and `T_K` [K]. Sets up a CR proton spectrum with energy slope `α_p` as a fraction `Xcr` of the thermal energy density. Returns emissivity in units [GeV cm^-3 s^-1 ]. See Pfrommer&Enßlin (2004), Eq. 19.

## Function Arguments:

  * `rho_cgs`: SPH particle density in [g/cm^3]
  * `T_K`: SPH particle temperature [K]
  * `α_p`: Slope of proton energy spectrum `S ~ 2.0 - 2.5`
  * `Eγ`: Photon energy [GeV]
  * `Xcr`: CR proton to thermal pressure ratio.
  * `xH`: Hydrogen mass fraction in the simulation

## Mapping settings

For mean value along line-of-sight:

  * `weights`: `rho` (weight with density)
  * `reduce_image`: `true`

For integral along line-of-sight, aka surface brightness:

  * `weights`: [`part_weight_physical`](@ref)
  * `reduce_image`: `false`
