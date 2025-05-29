```
GadgetPhysical(l_unit::T=3.085678e21, m_unit::T=1.989e43, v_unit::T=1.e5;
               a_scale::T=1.0, hpar::T=1.0,
               γ_th::T=5.0/3.0, xH::T=0.752) where T
```

Creates a struct `GadgetPhysical` which holds the conversion factors between comoving code units and physical units, without unit information.

Keyword arugments specify:

# Arguments

  * `a_scale::T = 1.0`:  Cosmological scale factor of the simulation. Can be passed with the header `h` as `h.time`.
  * `hpar::T = 1.0`:     Hubble constant as 'little h'. Can be passed with header `h` as `h.h0`.
  * `γ_th::T = 5.0/3.0`: Adiabatic index of gas.
  * `xH::T = 0.752`:      Hydrogen fraction of the simulation, if run without chemical model.

# Fields

| Name              | Meaning                            |
|:----------------- |:---------------------------------- |
| `x_cgs::T`        | position in cm                     |
| `x_physical::T`   | position in kpc                    |
| `v_cgs::T`        | velocity in cm/s                   |
| `v_physical::T`   | velocity in km/s                   |
| `m_cgs::T`        | mass in g                          |
| `m_msun::T`       | mass in Msun                       |
| `m_physical::T`   | mass in 10^10 Msun                 |
| `t_s::T`          | time in sec                        |
| `t_Myr::T`        | time in Myr                        |
| `E_cgs::T`        | energy in erg                      |
| `E_eV::T`         | energy in eV                       |
| `B_cgs::T`        | magnetic field in Gauss            |
| `rho_physical::T` | density in 10^10 Msun/kpc^3        |
| `rho_cgs::T`      | density in $g/cm^3$                |
| `rho_ncm3::T`     | density in $n_p/cm^3$              |
| `T_K::T`          | temperature in K                   |
| `T_eV::T`         | temperature in eV                  |
| `P_th_cgs::T`     | thermal pressure in Ba             |
| `P_CR_cgs::T`     | cosmic ray pressure in Ba          |
| `CR_norm::T`      | LMB*SPECTRAL*CRs Norm in cgs units |
