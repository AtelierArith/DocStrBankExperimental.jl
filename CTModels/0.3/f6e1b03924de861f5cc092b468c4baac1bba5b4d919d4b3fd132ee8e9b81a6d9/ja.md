```julia
costate(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, Co<:Function}
) -> Function

```

最適制御解のコスト状態を返します。

```@example
julia> t0 = time_grid(sol)[1]
julia> p  = costate(sol)
julia> p0 = p(t0)
```
