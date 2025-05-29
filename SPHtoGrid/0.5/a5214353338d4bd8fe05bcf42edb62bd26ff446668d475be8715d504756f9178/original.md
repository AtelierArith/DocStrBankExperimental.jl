```
analytic_synchrotron_emission( rho_cgs::Array{<:Real}, B_cgs::Array{<:Real},
                               T_K::Array{<:Real}, Mach::Array{<:Real};
                               xH::Real=0.76, dsa_model::Integer=1, ν0::Real=1.44e9,
                               integrate_pitch_angle::Bool=true )
```

Computes the analytic synchrotron emission with the simplified approach described in Longair Eq. 8.128. Returns J_ν in units [erg/cm^3/Hz/s].

# Arguments

  * `rho_cgs::Array{<:Real}`: Density in $g/cm^3$.
  * `B_cgs::Array{<:Real}`:   Magnetic field in Gauss.
  * `T_K::Array{<:Real}`:     Temperature in Kelvin.
  * `Mach::Array{<:Real}`:    Mach number.

## Keyword Arguments

  * `xH::Float64 = 0.76`:               Hydrogen fraction of the simulation, if run without chemical model.
  * `dsa_model::Integer=1`:             Diffuse-Shock-Acceleration model. Takes values `0...4`, see next section.
  * `ν0::Real=1.44e9`:                  Observation frequency in $Hz$.
  * `K_ep::Real=0.01`:                  Ratio of CR proton to electron energy density.
  * `integrate_pitch_angle::Bool=true`: Integrates over the pitch angle as in Longair Eq. 8.87.
  * `convert_to_mJy::Bool=false`:       Convert the result from $[erg/cm^3/Hz/s]$ to $mJy/cm$.

## DSA Models

Takes either your self-defined `AbstractShockAccelerationEfficiency` (see [DiffusiveShockAccelerationModels.jl](https://github.com/LudwigBoess/DiffusiveShockAccelerationModels.jl) for details!) or a numerical value as input. Numerical values correspond to:

  * `0`: [Kang et. al. (2007)](https://ui.adsabs.harvard.edu/abs/2007ApJ...669..729K/abstract)
  * `1`: [Kang & Ryu (2013)](https://ui.adsabs.harvard.edu/abs/2013ApJ...764...95K/abstract)
  * `2`: [Ryu et. al. (2019)](https://ui.adsabs.harvard.edu/abs/2019ApJ...883...60R/abstract)
  * `3`: [Caprioli & Spitkovsky (2014)](https://ui.adsabs.harvard.edu/abs/2014ApJ...783...91C/abstract)
  * `4`: [Pfrommer et. al. (2006)](https://ui.adsabs.harvard.edu/abs/2006MNRAS.367..113P/abstract)
