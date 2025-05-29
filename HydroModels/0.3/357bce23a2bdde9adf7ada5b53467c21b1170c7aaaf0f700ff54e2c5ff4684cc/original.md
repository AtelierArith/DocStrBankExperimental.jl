```
(flux::AbstractHydroFlux)(input::AbstractArray, params::ComponentVector; kwargs...)
```

Apply a HydroFlux model to input data for calculating water fluxes.

# Arguments

  * `input::AbstractArray`: Input data array with the following possible dimensions:

      * `Matrix`: Time series data with shape (variables, timesteps)
      * `Array{3}`: Distributed data with shape (variables, nodes, timesteps)
  * `params::ComponentVector`: Model parameters organized in a component vector
  * `kwargs`: Additional keyword arguments:

      * `ptyidx::AbstractVector{Int}`: Parameter type indices for distributed runs (default: all nodes)

# Returns

  * `Matrix`: For 2D input, returns matrix of shape (output_variables, timesteps)
  * `Array{3}`: For 3D input, returns array of shape (output_variables, nodes, timesteps)

# Description

This function applies the flux calculations to input time series data, supporting both  single-node and distributed (multi-node) simulations. For distributed runs, parameters  are automatically expanded to match the number of nodes.

## Input Data Structure

  * Variables must be arranged along the first dimension
  * For distributed runs, nodes are along the second dimension
  * Time steps are always in the last dimension

## Parameter Handling

  * Single-node: Parameters are used as is
  * Multi-node: Parameters are expanded using `ptyidx` to match node count
  * Component parameters maintain type stability

## Example

```julia
# Single-node simulation
flux = HydroFlux([P, E] => [Q], params=[k], exprs=[k*P - E])
output = flux(input, params)  # input: (2, timesteps)

# Multi-node simulation
output = flux(input, params, ptyidx=1:n_nodes)  # input: (2, n_nodes, timesteps)
```
