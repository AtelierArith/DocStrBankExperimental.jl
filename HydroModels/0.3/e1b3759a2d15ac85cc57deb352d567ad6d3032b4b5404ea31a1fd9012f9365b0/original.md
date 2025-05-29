```
(flux::UnitHydrograph)(input::AbstractArray, pas::ComponentVector; kwargs...)
```

Applies the Unit Hydrograph convolution to the input time series.

# Arguments

  * `input::AbstractArray{T,D}`: Input data. Shape can be `(variables, timesteps)` (D=2) or `(variables, nodes, timesteps)` (D=3).
  * `pas::ComponentVector`: Parameters for the unit hydrograph function (`uh_func`).

# Keyword Arguments

  * (for `:DISCRETE` solver): `solver`, `timeidx`, `interp`.
  * (for 3D input): `ptyidx` mapping parameters to nodes.

# Returns

  * `AbstractArray`: Routed output, with shape matching the input's time (and node, if D=3) dimensions: `(output_variables, timesteps)` or `(output_variables, nodes, timesteps)`.

# Example

```julia
# Assuming 'uh' is a UnitHydrograph instance
routed_flow = uh(input_runoff, parameters)
```

# Notes

  * Behavior depends on `solvetype` (`:DISCRETE` or `:SPARSE`) set during construction.
  * `:DISCRETE` uses an ODE solver approach (requires `solver` kwarg).
  * `:SPARSE` uses direct convolution via sparse matrices.
  * 3D input requires `ptyidx` and internally calls the 2D methods per node.
  * Single time point input (Vector) is not supported.
