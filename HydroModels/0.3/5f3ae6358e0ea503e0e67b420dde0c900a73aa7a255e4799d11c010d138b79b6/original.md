```
(flux::NeuralFlux)(input::AbstractArray, params::ComponentVector; kwargs...)
```

Apply a neural network-based flux model to input data for calculating water fluxes.

# Arguments

  * `input::AbstractArray`: Input data array with the following possible dimensions:

      * `Matrix`: Time series data with shape (variables, timesteps)
      * `Array{3}`: Distributed data with shape (variables, nodes, timesteps)
  * `params::ComponentVector`: Model parameters containing neural network weights and biases
  * `kwargs`: Additional keyword arguments:

      * `ptyidx::AbstractVector{Int}`: Parameter type indices for distributed runs (default: all nodes)

# Returns

  * `Matrix`: For 2D input, returns matrix of shape (output_variables, timesteps)
  * `Array{3}`: For 3D input, returns array of shape (output_variables, nodes, timesteps)

# Description

This function applies neural network-based flux calculations to input time series data,  supporting both single-node and distributed (multi-node) simulations. The neural network  parameters are automatically retrieved from the appropriate component of the parameter vector.

## Input Data Structure

  * Variables must be arranged along the first dimension
  * For distributed runs, nodes are along the second dimension
  * Time steps are always in the last dimension

## Parameter Handling

  * Neural network parameters are accessed via `params[:nns][chain_name]`
  * Parameters maintain their structure as defined in the neural network
  * For distributed runs, the same network is applied to each node

## Example

```julia
# Define neural network flux
flux = NeuralFlux(
    [P, E] => [Q],           # input/output structure
    Dense(2, 1, tanh)        # neural network architecture
)

# Single-node simulation
output = flux(input, params)  # input: (2, timesteps)

# Multi-node simulation
output = flux(input, params)  # input: (2, n_nodes, timesteps)
```

# Notes

  * Neural network parameters must be properly initialized before use
  * The neural network architecture must match the input/output dimensions
  * For distributed runs, the same network is shared across all nodes
