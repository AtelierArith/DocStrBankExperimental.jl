```
DiffusiveCFL(Δt)
```

Returns an object for computing the diffusive Courant-Freidrichs-Lewy (CFL) number associated with time step `Δt` or `TimeStepWizard` and the time scale for diffusion across a cell associated with `model.closure`.  The diffusive CFL, e.g., for viscosity is $ν Δt / Δx²$.

The maximum diffusive CFL number among viscosity and all tracer diffusivities is returned.

# Example

```jldoctest
julia> using Oceananigans

julia> model = NonhydrostaticModel(grid = RectilinearGrid(size=(16, 16, 16), extent=(1, 1, 1)),
                                   closure = ScalarDiffusivity(; ν = 1e-2));

julia> Δt = 0.1;

julia> dcfl = DiffusiveCFL(Δt);

julia> dcfl(model)
0.256
```
