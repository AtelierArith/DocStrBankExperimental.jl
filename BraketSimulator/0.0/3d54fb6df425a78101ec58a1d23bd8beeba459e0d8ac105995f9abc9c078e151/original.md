```
simulate(simulator::AbstractSimulator, circuit_ir::Union{OpenQasmProgram, Program}, shots::Int; kwargs...) -> GateModelTaskResult
```

Simulate the evolution of a state vector or density matrix using the passed-in `simulator`. The instructions to apply (gates and noise channels) and measurements to make are encoded in `circuit_ir`. Supported IR formats are `OpenQASMProgram` (OpenQASM3) and `Program` (JAQCD). Returns a `GateModelTaskResult` containing the individual shot measurements (if `shots > 0`), final calculated results, circuit IR, and metadata about the task.
