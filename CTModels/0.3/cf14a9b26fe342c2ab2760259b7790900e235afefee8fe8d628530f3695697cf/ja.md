```julia
state(
    sol::CTModels.Solution{<:CTModels.AbstractTimeGridModel, <:CTModels.AbstractTimesModel, <:CTModels.StateModelSolution{TS<:Function}}
) -> Function

```

最適制御解の状態（時間の関数）を返します。

```@example
julia> t0 = time_grid(sol)[1]
julia> x  = state(sol)
julia> x0 = x(t0)
```
