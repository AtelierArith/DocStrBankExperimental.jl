```
log_metric(metric_name::String, value::Union{Float64, Int}; timestamp=time(), iteration_number=nothing)
```

ジョブスクリプト内で、名前 `metric_name` と値 `value` を持つメトリックをログに記録します。これは後でジョブの*外部*で [`metrics`](@ref) を使って取得できます。メトリックは、例えば、各エポックでのトレーニングアルゴリズムの損失などが考えられます。
