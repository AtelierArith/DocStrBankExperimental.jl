```
energy_total_modified(q_global, equations, cache)
```

Return the modified total energy of the primitive variables `q_global` for the `equations`. This modified total energy is a conserved quantity and can contain additional terms compared to the usual [`energy_total`](@ref). For example, for the [`SvaerdKalischEquations1D`](@ref) and the [`SerreGreenNaghdiEquations1D`](@ref), it contains additional terms depending on the derivative of the velocity $v_x$ modeling non-hydrostatic contributions. For equations which are not `AbstractShallowWaterEquations`, the modified total energy does not have to be an extension of the usual [`energy_total`](@ref) and does not have to be related to a physical energy. However, it is still a conserved quantity for appropriate boundary conditions and may contain derivatives of the solution.

`q_global` is a vector of the primitive variables at ALL nodes. `cache` needs to hold the SBP operators used by the `solver` if non-hydrostatic terms are present.

Internally, this function allocates a vector for the output and calls [`DispersiveShallowWater.energy_total_modified!`](@ref).
