```
VJP_λ_∂SIA∂θ_continuous(
    θ,
    λ::Matrix{R},
    H::Matrix{R},
    simulation::SIM,
    t::R;
    batch_id::Union{Nothing, I} = nothing
)
```

Implementation of the continuous adjoint of the SIA2D equation with respect to θ. Given λ, H and θ, it returns the VJP of λ^T * ∂(SIA2D)/∂θ (θ).

Arguments:

  * `θ`: Vector of parameters
  * `λ::Matrix{R}`: Adjoint state, also called output gradient in reverse-mode AD.
  * `H::Matrix{R}`: Ice thickness which corresponds to the input state of the SIA2D.
  * `simulation::SIM`: Simulation parameters.
  * `t::R`: Time value, not used as SIA2D is time independent.
  * `batch_id::Union{Nothing, I}`: Batch index.

Returns:

  * `dλ::Matrix{R}`: Jacobian vector product, also called input gradient in reverse-mode AD.
