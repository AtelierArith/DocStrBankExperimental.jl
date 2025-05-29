```
GadgetPhysicalUnits(l_unit::T=3.085678e21, m_unit::T=1.989e43, v_unit::T=1.e5;
                    a_scale::T=1.0, hpar::T=1.0,
                    γ_th::T=5.0/3.0, xH::T=0.752) where T
```

Creates a struct `GadgetPhysicalUnits` which holds the conversion factors between comoving code units and physical units. Stores the unit information which can be converted with Unitful or UnitfulAstro.

# Keyword Arguments

  * `a_scale::T = 1.0`:  Cosmological scale factor of the simulation. Can be passed with the header `h` as `h.time`.
  * `hpar::T = 1.0`:     Hubble constant as 'little h'. Can be passed with header `h` as `h.h0`.
  * `γ_th::T = 5.0/3.0`: Adiabatic index of gas.
  * `xH::T = 0.752`:      Hydrogen fraction of the simulation, if run without chemical model.

# Fields

| Name                      | Meaning                            |
|:------------------------- |:---------------------------------- |
| `x_cgs::Quantity{T}`      | position in cm                     |
| `x_physical::Quantity{T}` | position in kpc                    |
| `v_cgs::Quantity{T}`      | velocity in cm/s                   |
| `v_physical::Quantity{T}` | velocity in km/s                   |
| `m_cgs::Quantity{T}`      | mass in g                          |
| `m_msun::Quantity{T}`     | mass in solar masses               |
| `t_s::Quantity{T}`        | time in sec                        |
| `t_Myr::Quantity{T}`      | time in Myr                        |
| `E_cgs::Quantity{T}`      | energy in erg                      |
| `E_eV::Quantity{T}`       | energy in eV                       |
| `B_cgs::Quantity{T}`      | magnetic field in Gauss            |
| `rho_cgs::Quantity{T}`    | density in $g/cm^3$                |
| `rho_ncm3::Quantity{T}`   | density in $n_p/cm^3$              |
| `T_K::Quantity{T}`        | temperature in K                   |
| `T_eV::Quantity{T}`       | temperature in eV                  |
| `P_th_cgs::Quantity{T}`   | thermal pressure in Ba             |
| `P_CR_cgs::Quantity{T}`   | cosmic ray pressure in Ba          |
| `CR_norm::Quantity{T}`    | LMB*SPECTRAL*CRs Norm in cgs units |
