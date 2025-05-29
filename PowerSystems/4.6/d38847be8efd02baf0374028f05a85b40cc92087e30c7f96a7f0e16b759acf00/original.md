```
mutable struct KauraPLL <: FrequencyEstimator
    ω_lp::Float64
    kp_pll::Float64
    ki_pll::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Phase-Locked Loop (PLL) based on ["Operation of a phase locked loop system under distorted utility conditions"](https://doi.org/10.1109/28.567077) by Vikram Kaura, and Vladimir Blasko

# Arguments

  * `ω_lp::Float64`: PLL low-pass filter frequency (rad/sec), validation range: `(0, nothing)`
  * `kp_pll::Float64`: PLL proportional gain, validation range: `(0, nothing)`
  * `ki_pll::Float64`: PLL integral gain, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the KauraPLL model are:

```
vd_pll: d-axis of the measured voltage in the PLL synchronous reference frame (SRF),
vq_pll: q-axis of the measured voltage in the PLL SRF,
ε_pll: Integrator state of the PI controller,
θ_pll: Phase angle displacement in the PLL SRF
```

  * `n_states::Int`: (**Do not modify.**) KauraPLL has 4 states
