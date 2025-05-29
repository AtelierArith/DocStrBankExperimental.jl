```
λγ_PE04(rho_cgs::Real, T_K::Real, α_p::Real; 
        Xcr::Real=0.5,
        Eγ_π0_min::Real=0.1, Eγ_π0_max::Real=200.0,
        xH::Real=0.752)
```

Number of γ-ray photons produced per time and volume from a proton spectrum given as a fraction `Xcr` of the energy density defined by `rho_cgs` [g/cm^3] and `T_K` [K], with a powerlaw slope in energy `α_p`. Integrated between photon energies `Eγ_π0_min` and `Eγ_π0_max` [GeV]. Returns number of photons in energy band in units of [γ cm^-3 s^-1]. See Pfrommer&Enßlin (2004), Eq. 25.

## Function Arguments:

  * `rho_cgs`: SPH particle density in [g/cm^3]
  * `T_K`: SPH particle temperature [K]
  * `α_p`: Slope of proton energy spectrum `S ~ 2.0 - 2.5`
  * `Xcr`: CR proton to thermal pressure ratio.
  * `Eγ_π0_min`: Minimum photon energy for γ-ray spectrum [GeV]
  * `Eγ_π0_max`: Maximum photon energy for γ-ray spectrum [GeV]
  * `xH`: Hydrogen mass fraction in the simulation

## Mapping settings

For mean value along line-of-sight:

  * `weights`: `rho` (weight with density)
  * `reduce_image`: `true`

For integral along line-of-sight, aka surface brightness:

  * `weights`: [`part_weight_physical`](@ref)
  * `reduce_image`: `false`
