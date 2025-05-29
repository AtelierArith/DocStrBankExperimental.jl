```
compile_workflow(workflow::String, build_dir::String)
```

Given a path for the workflow and an accessible location for the build directory, this function compiles the XML workflow.

Note:   workflow => absolute path to the xpnet file   build_dir => path to build directory

# Examples

```julia-repl
tmp_dir = joinpath(@__DIR, "tmp")
julia> compile_workflow(joinpath(tmp_dir, "hello_julia.xpnet"))
...
Success: Workflow compiled

```

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref), [`generate_workflow`](@ref).
