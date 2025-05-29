```julia
mutable struct CVSweepResult <: LiquidElectrolytes.AbstractSimulationResult
```

Result type for [`cvsweep`](@ref).

Fields:

  * `voltages::Any`: Vector of voltages

  * `times::Any`: Vector of times

  * `j_reaction::Any`: Working electrode molar reaction rates

  * `j_bulk::Any`: Bulk molar fluxes

  * `j_we::Any`: Working electrode molar fluxes

  * `tsol::Any`: Transient solution

Access methods: [`voltages`](@ref), [`currents`](@ref)  [`voltages_currents`](@ref)
