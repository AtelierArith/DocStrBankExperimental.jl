```julia
objective(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.AbstractControlModel, <:CTModels.AbstractVariableModel, <:Function, O<:Real}
) -> Real

```

最適制御解の目的値を返します。
