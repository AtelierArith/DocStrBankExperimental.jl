```julia
export_ocp_solution(args...; format, kwargs...)

```

JLDまたはJSON形式でソリューションをエクスポートします。

# 例

```julia-repl
julia> CTModels.export_ocp_solution(sol; filename="solution", format=:JSON)
julia> CTModels.export_ocp_solution(sol; filename="solution", format=:JLD)
```
