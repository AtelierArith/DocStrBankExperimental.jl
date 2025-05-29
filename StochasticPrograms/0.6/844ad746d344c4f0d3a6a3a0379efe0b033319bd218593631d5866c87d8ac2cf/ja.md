```
StochasticProgram(::Type{Scenario},
                  instantiation::StochasticInstantiation,
                  optimizer_constructor=nothing) where Scenario <: AbstractScenario
```

新しい二段階確率プログラムを作成します。シナリオのタイプは `Scenario` で、ステージデータはありません。オプションで、後で確率プログラムを最適化するために、適切な `optimizer_constructor` を指定することができます。
