```julia
mutable struct IVSweepResult <: LiquidElectrolytes.AbstractSimulationResult
```

Result data type for [`ivsweep`](@ref)

  * `voltages::Any`: Vector of voltages

  * `j_reaction::Any`: Working electrode molar reaction rates

  * `j_we::Any`: Working electrode molar fluxes

  * `j_bulk::Any`: Bulk molar fluxes

  * `solutions::Any`: Vector of solutions

Access methods: [`voltages`](@ref), [`currents`](@ref),  [`voltages_currents`](@ref), [`voltages_solutions`](@ref)
