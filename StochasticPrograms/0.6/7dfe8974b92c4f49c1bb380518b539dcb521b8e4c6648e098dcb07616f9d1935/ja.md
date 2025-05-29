```
StochasticProgram(first_stage_params::Any,
                  second_stage_params::Any,
                  ::Type{Scenario},
                  instantiation::StochasticInstantiation,
                  optimizer_constructor=nothing) where Scenario <: AbstractScenario
```

新しい二段階確率プログラムを作成します。ステージデータは `first_stage_params` と `second_stage_params` で与えられます。構築後、タイプ `S` のシナリオを `add_scenario!` を通じて追加できます。オプションで、後で確率プログラムを最適化するために、適切な `optimizer_constructor` を提供できます。複数のJuliaプロセスが利用可能な場合、結果の確率プログラムはこれらのプロセスに自動的にメモリ分散されます。これを回避するには、`procs = [1]` を設定します。
