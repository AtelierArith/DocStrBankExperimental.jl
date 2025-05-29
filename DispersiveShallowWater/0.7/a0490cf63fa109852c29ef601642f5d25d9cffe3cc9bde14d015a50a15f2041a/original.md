```
hamiltonian(q_global, equations, cache)
```

Return the Hamiltonian of the primitive variables `q_global` for the `equations`. The Hamiltonian is a conserved quantity and may contain derivatives of the solution.

`q_global` is a vector of the primitive variables at ALL nodes. `cache` needs to hold the SBP operators used by the `solver` if non-hydrostatic terms are present.

Internally, this function allocates a vector for the output and calls [`DispersiveShallowWater.hamiltonian!`](@ref).

!!! note
    This function is not necessarily implemented for all equations. See [`DispersiveShallowWater.hamiltonian!`](@ref) for further details of equations supporting it.

