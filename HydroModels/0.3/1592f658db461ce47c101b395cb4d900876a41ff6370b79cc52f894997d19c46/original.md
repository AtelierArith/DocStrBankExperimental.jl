```
(bucket::NeuralBucket)(input::AbstractArray{T,3}, pas::ComponentVector; kwargs...) where {T,N}
```

Apply a neural bucket model to input data for calculating water fluxes and state updates over time.

# Arguments

  * `input::AbstractArray{T,3}`: Input data array with shape (variables, nodes, timesteps).
  * `pas::ComponentVector`: Model parameters containing both regular parameters and initial states.
  * `kwargs`: Additional keyword arguments:

      * `ptyidx::AbstractVector{Int}`: Parameter type indices for distributed runs (default: all nodes).
      * `styidx::AbstractVector{Int}`: State type indices for distributed runs (default: all nodes).
      * `initstates::ComponentVector`: Initial state values (default: zeros for all states).

# Returns

  * `Array{T,3}`: Output array with shape (output_variables, nodes, timesteps).

# Description

This function applies the neural bucket's recurrent model to input time series data, supporting distributed (multi-node) simulations. The function handles state updates internally through the recurrent neural network architecture.

The input array must have variables arranged along the first dimension, nodes along the second dimension, and time steps along the third dimension.
