```julia
variable(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.VariableModelSolution{TS<:Union{Real, AbstractVector{<:Real}}}}
) -> Union{Real, AbstractVector{<:Real}}

```

Return the variable of the optimal control solution or `nothing`.

```@example
julia> v  = variable(sol)
```
