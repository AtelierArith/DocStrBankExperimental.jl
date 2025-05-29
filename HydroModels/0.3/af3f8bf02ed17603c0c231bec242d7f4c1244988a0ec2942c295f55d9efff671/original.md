```
(bucket::HydroBucket{N,S})(input::AbstractArray{T,2}, params::ComponentVector; kwargs...)
(bucket::HydroBucket{N,S})(input::AbstractArray{T,3}, params::ComponentVector; kwargs...)
```

Evaluate the HydroBucket model with input data and parameters.

# Arguments

  * `input`: Array of input data. Use 2D (variables × time) for single node, or 3D (variables × nodes × time) for multiple nodes.
  * `params`: ComponentVector of model parameters and initial states.
  * `kwargs`: Optional keyword arguments (e.g., solver, interp, timeidx, ptyidx, styidx, initstates).

# Returns

  * Output array: (states+outputs) × time (2D) or (states+outputs) × nodes × time (3D).
  * For 2D input: Array of size (states+outputs) × time
  * For 3D input: Array of size (states+outputs) × nodes × time

# Description

This function executes the bucket model by:

1. Setting up interpolation for input time series
2. Preparing parameters and initial states
3. Solving ODEs if the model has state variables (S=true)
4. Computing fluxes using the model's flux functions
5. Combining states and fluxes into the output array

## Single Node Operation (2D input)

  * Processes one location's time series
  * Uses provided parameters and initial states
  * Solves ODEs if model has states
  * Returns combined states and fluxes

## Multi-Node Operation (3D input)

  * Processes multiple locations simultaneously
  * Supports both shared and distributed parameters
  * Handles state evolution for each node
  * Returns results for all nodes
