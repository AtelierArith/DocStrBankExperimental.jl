```
run_reopt(ms::AbstractArray{T, 1}, d::Dict) where T <: JuMP.AbstractModel
```

`Scenario` と `BAUScenario` を並行して解決し、`ms` の最初の 2 つの (空の) モデルと `d` からの入力を使用します。
