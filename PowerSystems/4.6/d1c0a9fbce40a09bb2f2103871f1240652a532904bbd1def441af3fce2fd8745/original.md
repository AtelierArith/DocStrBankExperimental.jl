```
mutable struct ReducedOrderPLL <: FrequencyEstimator
    ω_lp::Float64
    kp_pll::Float64
    ki_pll::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Phase-Locked Loop (PLL) based on ["Reduced-order Structure-preserving Model for Parallel-connected Three-phase Grid-tied Inverters."](https://doi.org/10.1109/COMPEL.2017.8013389)

# Arguments

  * `ω_lp::Float64`: PLL low-pass filter frequency (rad/sec), validation range: `(0, nothing)`
  * `kp_pll::Float64`: PLL proportional gain, validation range: `(0, nothing)`
  * `ki_pll::Float64`: PLL integral gain, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ReducedOrderPLL model are:

```
vq_pll: q-axis of the measured voltage in the PLL synchronous reference frame (SRF),
ε_pll: Integrator state of the PI controller,
θ_pll: Phase angle displacement in the PLL SRF
```

  * `n_states::Int`: (**Do not modify.**) ReducedOrderPLL has 3 states
