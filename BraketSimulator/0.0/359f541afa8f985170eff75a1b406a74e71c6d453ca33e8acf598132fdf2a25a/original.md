```
simulate(simulator::AbstractSimulator, circuit_irs::Vector{<:Union{Program, OpenQasmProgram}}, shots::Int; max_parallel::Int=min(32, Threads.nthreads()), inputs=Dict{String,Float64}(), kwargs...) -> Vector{GateModelTaskResult}
```

Simulate the evolution of a *batch* of state vectors or density matrices using the passed in `simulator`. The instructions to apply (gates and noise channels) and measurements to make are encoded in `circuit_irs`. Supported IR formats are `OpenQASMProgram` (OpenQASM3) and `Program` (JAQCD).

The simulation of the batch is done in parallel using threads. The keyword argument `max_parallel` specifies the number of evolutions to simulate in parallel – the default value is whichever of `32` and `Threads.nthreads()` is smaller. This is to avoid overwhelming the thread scheduler with too many small tasks waiting to run, as each evolution is itself threaded. This value may change in the future.

The `inputs` keyword argument can be a `Dict{String}` or a `Vector{Dict{String}}`. In the first case, the same input values are applied to all `circuit_irs`. In the second, the length of the `inputs` *must* be the same as the length of `circuit_irs`, and the `n`-th `inputs` is applied to the `n`-th `circuit_irs`.

Returns a `Vector{GateModelTaskResult}`, each element of which contains the individual shot measurements (if `shots > 0`), final calculated results, corresponding circuit IR, and metadata about the task.
