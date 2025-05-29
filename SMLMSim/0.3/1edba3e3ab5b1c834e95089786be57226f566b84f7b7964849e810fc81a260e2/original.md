```
simulate(sim::AbstractSim; kwargs...)
```

Generic interface for all simulation types. Dispatches to the appropriate method based on the concrete simulation type.

# Arguments

  * `sim::AbstractSim`: The simulation configuration object
  * `kwargs...`: Additional keyword arguments specific to the simulation type

# Returns

  * The result of the specific simulation method

# Example

```julia
# Create a static SMLM simulation configuration
params = StaticSMLMParams(
    density = 1.0,        # Changed from ρ to density
    σ_psf = 0.13
)

# Run the simulation
results = simulate(params)
```
