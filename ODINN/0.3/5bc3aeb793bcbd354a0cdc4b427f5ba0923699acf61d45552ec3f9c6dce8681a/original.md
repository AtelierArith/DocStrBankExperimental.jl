```
Diffusivity(target::SIA2D_D_target; H, ∇S, θ, iceflow_model, ml_model, glacier, params)
```

Compute the effective diffusivity field for a 2D shallow ice model using the diagnostic `target` and  a predicted velocity matrix `U`.

This function uses a learned or specified model to estimate the velocity matrix `U`, then calculates the diffusivity as either `H .* U` (if dimensions match) or the averaged `H` times `U` if dimensions differ by one grid cell (staggered grid). Errors if dimensions are incompatible.

# Arguments

  * `target::SIA2D_D_target`: Diagnostic target object defining interpolation and scaling rules.

# Keyword Arguments

  * `H`: Ice thickness.
  * `∇S`: Ice surface slope.
  * `θ`: Parameters of the model.
  * `iceflow_model`: Iceflow model used for simulation.
  * `ml_model`: Machine learning model used for simulation.
  * `glacier`: Glacier data.
  * `params`: Model parameters.

# Returns

  * A matrix of diffusivity values with the same shape as `H` or staggered by one cell, depending on `U`.

# Throws

  * An error if the dimensions of `U` and `H` are not compatible for diffusivity calculation.

# Notes

Uses `predict_U_matrix` internally to obtain velocity-like terms. Supports both grid-matched  and staggered configurations by averaging `H` where necessary.
