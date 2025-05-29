```
get_objective(mp::AbstractManoptProblem, recursive=false)
```

return the objective [`AbstractManifoldObjective`](@ref) stored within an [`AbstractManoptProblem`](@ref). If `recursive is set to true, it additionally unwraps all decorators of the objective`
