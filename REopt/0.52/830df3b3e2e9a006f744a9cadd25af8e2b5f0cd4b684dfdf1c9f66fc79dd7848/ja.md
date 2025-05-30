```
run_reopt(ms::AbstractArray{T, 1}, p::REoptInputs) where T <: JuMP.AbstractModel
```

`ms`の最初の2つの（空の）モデルと`p`からの入力を使用して、`Scenario`と`BAUScenario`を並行して解決します。
