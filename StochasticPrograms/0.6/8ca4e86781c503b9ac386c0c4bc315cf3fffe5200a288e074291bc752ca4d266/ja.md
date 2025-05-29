```
StochasticProgram(first_stage_params::Any,
                  second_stage_params::Any,
                  scenarios::Vector{<:AbstractScenario},
                  instantiation::StochasticInstantiation,
                  optimizer_constructor = nothing)
```

与えられた `scenarios` のコレクションを使用して新しい二段階確率プログラムを作成します。オプションで、後で確率プログラムを最適化するために有能な `optimizer_constructor` を提供できます。複数のJuliaプロセスが利用可能な場合、結果の確率プログラムはこれらのプロセスに自動的にメモリ分散されます。これを回避するには、`procs = [1]` を設定します。
