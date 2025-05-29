```
set_objective_sense(model::Model, sense::MOI.OptimizationSense)
```

モデルの目的の感覚を指定された感覚に設定します。目的関数を設定するには、[`set_objective_function`](@ref)を参照してください。これらは低レベルの関数です。目的を設定する推奨方法は、[`@objective`](@ref)マクロを使用することです。
