```
simulate(d::LocalSimulator, task_spec::Union{Circuit, AbstractProgram}, args...; shots::Int=0, inputs::Dict{String, Float64} = Dict{String, Float64}(), kwargs...)
```

Simulate the execution of `task_spec` using the backend of [`LocalSimulator](@ref) `d`. `args` are additional arguments to be provided to the backend. `inputs` is used to set the value of any [`FreeParameter`](@ref) in `task_spec` and will override the existing `inputs` field of an `OpenQasmProgram`. Other `kwargs` will be passed to the backend simulator. Returns a [`LocalQuantumTask`](@ref Braket.LocalQuantumTask).
