```
gamma_luminosity_pions_PE04(rho_cgs::Real, m_cgs::Real, T_K::Real, α_p::Real;
                            Xcr::Real=0.5,
                            Eγ_π0_min::Real=0.1, Eγ_π0_max::Real=200.0,
                            xH::Real=0.752)
```

γ-ray luminosity produced from a proton spectrum given as a fraction `Xcr` of the energy density defined by `rho_cgs` [g/cm^3] and `T_K` [K],  with a powerlaw slope in energy `α_p`. Integrated over SPH particle volume for particle of mass `m_cgs` [g]. Integrated between photon energies `Eγ_π0_min` and `Eγ_π0_max` [GeV]. Returns total luminosity integrated over energy band in units of [GeV s^-1]. See Pfrommer&Enßlin (2004), Eq. 25.

## Arguments:

  * `rho_cgs`: SPH particle density in [g/cm^3]
  * `m_cgs`: SPH particle mass in [g]
  * `T_K`: SPH particle temperature [K]
  * `α_p`: Slope of proton energy spectrum `S ~ 2.0 - 2.5`
  * `Xcr`: CR proton to thermal pressure ratio.
  * `Eγ_π0_min`: Minimum photon energy for γ-ray spectrum [GeV]
  * `Eγ_π0_max`: Maximum photon energy for γ-ray spectrum [GeV]
  * `xH`: Hydrogen mass fraction in the simulation

## Mapping settings

  * weight function: [`part_weight_one`](@ref)
  * reduce image: `true`
