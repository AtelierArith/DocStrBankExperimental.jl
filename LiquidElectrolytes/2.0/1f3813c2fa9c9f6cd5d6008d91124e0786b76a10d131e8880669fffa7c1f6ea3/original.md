```julia
struct DLCapSweepResult <: LiquidElectrolytes.AbstractSimulationResult
```

Result data type for [`dlcapsweep`](@ref)

  * `voltages::Vector`: Vector of voltages

  * `dlcaps::Vector`: Vector of double layer capacitances

  * `solutions::Vector`: Vector of solutions

Access methods: [`voltages`](@ref), [`voltages_solutions`](@ref),  [`voltages_dlcaps`](@ref)
