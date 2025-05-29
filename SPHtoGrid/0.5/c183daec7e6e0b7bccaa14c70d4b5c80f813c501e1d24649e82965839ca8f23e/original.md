```
analytic_synchrotron(P_cgs::Array{<:Real}, B_cgs::Array{<:Real}, 
                     Mach::Array{<:Real}, θ_B::Union{Nothing,Array{<:Real}}=nothing;
                     dsa_model::Union{Integer,AbstractShockAccelerationEfficiency}=1, 
                     ν0::Real=1.4e9,
                     K_ep::Real=0.01, CR_Emin::Real=1.0,
                     spectrum::Union{Nothing,Function}=nothing,
                     integrate_pitch_angle::Bool=true,
                     polarisation::Bool=false,
                     show_progress::Bool=false)
```

Computes the analytic synchrotron emission from a spectrum of electrons by explicitly integrating over the distribution function. The integral over the spectrum must be normalized to 1. The total energy density of the relativistic electrons is given by the CR to thermal pressure ratio obtained by employing a DSA model and computing Xcr as in [Pfrommer et. al. (2017)](https://ui.adsabs.harvard.edu/abs/2017MNRAS.465.4500P/abstract).

Returns synchrotron emissivity `j_nu` in units `[erg/s/Hz/cm^3]`.

# Arguments

  * `P_cgs::Array{<:Real}`:   Thermal energy density in `erg/cm^3`.
  * `B_cgs::Array{<:Real}`:   Magnetic field in Gauss.
  * `Mach::Array{<:Real}`:    Mach number.
  * `θ_B::Union{Nothing,Array{<:Real}}=nothing`: Shock obliquity (optional).

## Keyword Arguments

  * `ν0::Real=1.4e9`:           Observation frequency in `Hz`.
  * `dsa_model`:      Diffusive Shock Acceleration model. Takes values `0...4`, or custom model. See next section.
  * `K_ep::Real=0.01`:           Ratio of CR proton to electron energy acceleration.
  * `CR_Emin::Real=1`:           Injection energy of CR electron population in `GeV`.
  * `spectrum::Union{Nothing,Function}=nothing`: Spectrum function. Must be normalized so that the integral over it is 1.
  * `integrate_pitch_angle::Bool=true`: Optional avoid pitch angle integration to reduce computational cost.
  * `polarisation::Bool=false`: Set to `true` if you want to compute the polarized emission instead of the total intensity.
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
