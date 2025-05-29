```
getSignal(instantiatedModel::Modia.InstantiatedModel|result::Modia.Result, name::String)
```

インスタンス化されたモデルに存在する結果の信号 `name` を返します（つまり、[`SignalTables.Var`](@ref)、[`SignalTables.Par`](@ref) または [`SignalTables.Map`](@ref)）。`name` が存在しない場合、エラーが発生します。
