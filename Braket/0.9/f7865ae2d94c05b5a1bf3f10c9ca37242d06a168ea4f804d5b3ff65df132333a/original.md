```
simulate(d::LocalSimulator, task_specs::Vector{T}, args...; kwargs...) where {T}
```

Simulate the execution of a *batch* of tasks specified by `task_specs` using the backend of [`LocalSimulator](@ref) `d`. `args` are additional arguments to be provided to the backend.

`kwargs` used by the `LocalSimulator` are:

  * `shots::Int` - the number of shots to run for all tasks in `task_specs`. Default is `0`.
  * `max_parallel::Int` - the maximum number of simulations to execute simultaneously. Default is `32`.
  * `inputs::Union{Vector{Dict{String, Float64}}, Dict{String, Float64}}` - used to set the value of any [`FreeParameter`](@ref) in each task specification. It must either be a `Dict` or a single-element `Vector` (in which case the same parameter values are used for all elements of `task_specs` *or* of the same length as `task_specs` (in which case the `i`-th  specification is paired with the `i`-th input dictionary). Default is an empty dictionary.

Other `kwargs` are passed through to the backend simulator. Returns a [`LocalQuantumTaskBatch`](@ref Braket.LocalQuantumTaskBatch).

!!! note
    Because Julia uses dynamic threading and `Task`s can migrate between threads, each simulation is a `Task` which itself can spawn many more `Task`s, as the internal implementation of [`LocalSimulator`](@ref)'s backend may use threading where appropriate. On systems with many CPU cores, spawning too many `Task`s may overwhelm the Julia scheduler and degrade performance. "Too many" depends on the particulars of your hardware, so on many-core systems you may need to tune this value for best performance.

