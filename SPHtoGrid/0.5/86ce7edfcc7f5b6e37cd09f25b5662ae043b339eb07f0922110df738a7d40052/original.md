```
x_ray_emissivity(T_keV::Vector{<:Real}, 
                 rho_cgs::Vector{<:Real},
                 metalicity::Union{Vector{Float64, Nothing}}=nothing; 
                 E0::Real=0.1, E1::Real=2.4, 
                 xH::Real=0.752,
                 cooling_function::Bool=false,
                 z::Real=0.0)
```

X-Ray emissivity for particles with temperature `T_keV` in $keV$, and density `rho_cgs` in $g/cm^3$. If available you can also add the `metalicity` in the gas. `Emin` and `Emax` give the minimum and maximum energy of the oberservation. `xH` gives the hydrogen fraction used in the simulation.

# Returns

X-Ray emissivity in units of [erg/s/cm^3].

## Arguments:

  * `T_keV`: SPH particle temperature [keV]
  * `m_cgs`: SPH particle mass in [g]
  * `rho_cgs`: SPH particle density in [g/cm^3]
  * `E0`: Minimum photon energy for Xray spectrum [keV]
  * `E1`: Maximum photon energy for Xray spectrum [keV]
  * `xH`: Hydrogen mass fraction in the simulation

## Mapping settings

  * weight function: [`part_weight_physical`](@ref)
  * reduce image: `false`
