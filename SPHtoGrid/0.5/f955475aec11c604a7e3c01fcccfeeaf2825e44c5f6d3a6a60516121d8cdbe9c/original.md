```
analytic_synchrotron_HB07( rho_cgs::Array{<:Real}, m_cgs::Array{<:Real}, hsml_cgs::Array{<:Real},
                           B_cgs::Array{<:Real}, T_keV::Array{<:Real}, Mach::Array{<:Real},
                           θ_B::Union{Nothing, Array{<:Real}}=nothing;
                           xH::Real=0.752, ν0::Real=1.4e9, z::Real=0.0,
                           dsa_model::Union{Nothing,Integer,AbstractShockAccelerationEfficiency}=nothing,
                           ξe::Real=1.e-5,
                           show_progress::Bool=false )
```

Computes the analytic synchrotron emission with the simplified approach described in [Hoeft&Brüggen (2007)](https://ui.adsabs.harvard.edu/abs/2007MNRAS.375...77H/abstract), following approach by [Wittor et. al. (2017)](https://ui.adsabs.harvard.edu/abs/2017MNRAS.464.4448W/abstract).

Returns synchrotron emissivity `j_nu` in units [erg/s/Hz/cm^3].

## Arguments

  * `rho_cgs::Array{<:Real}`:  Density in $g/cm^3$.
  * `m_cgs::Array{<:Real}`:    Particle mass in $g$.
  * `hsml_cgs::Array{<:Real}`: `HSML` block in $cm$.
  * `B_cgs::Array{<:Real}`:    Magnetic field in $G$.
  * `T_keV::Array{<:Real}`:    Temperature in $keV$.
  * `Mach::Array{<:Real}`:     Sonic Mach number.
  * `θ_B::Union{Nothing,Array{<:Real}}=nothing`: Shock obliquity (optional).

## Keyword Arguments

  * `xH::Float64 = 0.76`:        Hydrogen fraction of the simulation, if run without chemical model.
  * `ν0::Real=1.44e9`:           Observation frequency in $Hz$.
  * `z::Real=0.0`:               Redshift of the simulation.
  * `dsa_model=nothing`:         Diffusive Shock Acceleration model. If set to a value overwrites the default Hoeft&Brüggen acceleration model. See next section.
  * `ξe::Real=1.e-5`:            Ratio of CR proton to electron energy acceleration. Given as a fraction of thermal gas, essenitally `Xcr * Kep`.                               Default value from Nuza+2017. For `dsa_model != nothing` use something like `ξe = 1.e-4`.
  * `show_progress::Bool=false`: Enables a progress bar if set to true.

## DSA Models

Takes either your self-defined `AbstractShockAccelerationEfficiency` (see [DiffusiveShockAccelerationModels.jl](https://github.com/LudwigBoess/DiffusiveShockAccelerationModels.jl) for details!) or a numerical value as input. Numerical values correspond to:

  * `0`: [Kang et. al. (2007)](https://ui.adsabs.harvard.edu/abs/2007ApJ...669..729K/abstract)
  * `1`: [Kang & Ryu (2013)](https://ui.adsabs.harvard.edu/abs/2013ApJ...764...95K/abstract)
  * `2`: [Ryu et. al. (2019)](https://ui.adsabs.harvard.edu/abs/2019ApJ...883...60R/abstract)
  * `3`: [Caprioli & Spitkovsky (2014)](https://ui.adsabs.harvard.edu/abs/2014ApJ...783...91C/abstract)
  * `4`: [Pfrommer et. al. (2006)](https://ui.adsabs.harvard.edu/abs/2006MNRAS.367..113P/abstract)

## Mapping settings

  * weight function: [`part_weight_physical`](@ref)
  * reduce image: `false`
