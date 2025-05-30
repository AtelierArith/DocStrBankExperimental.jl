```julia
variable(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.VariableModelSolution{TS<:Union{Real, AbstractVector{<:Real}}}}
) -> Union{Real, AbstractVector{<:Real}}

```

最適制御解の変数を返すか、`nothing`を返します。

```@example
julia> v  = variable(sol)
```
