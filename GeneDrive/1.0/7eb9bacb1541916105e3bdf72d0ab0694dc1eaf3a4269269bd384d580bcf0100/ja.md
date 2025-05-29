```
solve_decision_model(model::JuMP.Model, objective_function::Nothing=nothing; kwargs...)
```

デフォルトの目的関数 `@objective(model, Min, 0)` を使用して数学的プログラムを解決します。これにより、動的人口モデルの出力と比較することができます。
