```julia
export_ocp_solution(args...; format, kwargs...)

```

Export a solution in JLD or JSON formats.

# Examples

```julia-repl
julia> CTModels.export_ocp_solution(sol; filename="solution", format=:JSON)
julia> CTModels.export_ocp_solution(sol; filename="solution", format=:JLD)
```
