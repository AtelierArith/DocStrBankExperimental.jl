```
VJP_λ_∂SIA_discrete(
    ∂dH::Matrix{R},
    H::Matrix{R},
    simulation::SIM,
    t::R;
    batch_id::Union{Nothing, I} = nothing
)
```

Compute an out-of-place adjoint step of the Shallow Ice Approximation PDE. Given an output gradient, it backpropagates the gradient to the inputs H and A. To some extent, this function is equivalent to VJP*λ*∂SIA∂H*continuous and VJP*λ*∂SIA∂θ*continuous.

Arguments:

  * `∂dH::Matrix{R}`: Output gradient to backpropagate.
  * `H::Matrix{R}`: Ice thickness which corresponds to the input state of the SIA2D.
  * `simulation::SIM`: Simulation parameters.
  * `t::R`: Time value, not used as SIA2D is time independent.
  * `batch_id::Union{Nothing, I}`: Batch index.

Returns:

  * `∂H::Matrix{R}`: Input gradient wrt H.
  * `∂A::F`: Input gradient wrt A.
