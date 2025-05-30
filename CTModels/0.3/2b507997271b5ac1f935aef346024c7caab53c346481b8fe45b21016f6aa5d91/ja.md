```julia
control(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.AbstractStateModel, <:CTModels.ControlModelSolution{TS<:Function}}
) -> Function

```

最適制御解の制御（時間の関数）を返します。

```@example
julia> t0 = time_grid(sol)[1]
julia> u  = control(sol)
julia> u0 = u(t0) # 初期時刻での制御
```
