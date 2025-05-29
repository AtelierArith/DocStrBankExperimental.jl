```
Job(p::Program; kwargs...)
Job(p::Program, inputs; kwargs...)
Job(p::Program, inputs, outputs; kwargs...)
```

Create `Job` by using `Program` from Pipelines.jl package. The 3 methods are wrappers around `run(::Program, ...)` defined in Pipelines.jl.

`kwargs...` include keyword arguments of `Job(::BaseAbstractCmd, ...)` and `run(::Program, ...)`.

See also: [`run`](@ref)
