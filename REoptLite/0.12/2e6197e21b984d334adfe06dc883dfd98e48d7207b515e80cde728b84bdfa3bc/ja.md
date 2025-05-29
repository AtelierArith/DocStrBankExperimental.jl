```
run_reopt(ms::AbstractArray{T, 1}, fp::String) where T <: JuMP.AbstractModel
```

`Scenario` と `BAUScenario` を並行して解決します。`ms` の最初の2つの（空の）モデルと、ファイルパス `fp` にあるJSONファイルで定義された入力を使用します。
