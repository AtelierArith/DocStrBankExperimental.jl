```
step!(sm::PMCSimulation)::PMCSimulation
```

Advance the simulation by one step.

Calling [`solve!`](@ref) will advance the simulation until the last step or the wall time is exceeded. When completing the simulation without calling [`solve!`](@ref), the simulation report needs to be finalised by calling [`Rimu.finalize_report!`](@ref).

See also [`ProjectorMonteCarloProblem`](@ref), [`init`](@ref), [`solve!`](@ref), [`solve`](@ref), [`Rimu.PMCSimulation`](@ref).
