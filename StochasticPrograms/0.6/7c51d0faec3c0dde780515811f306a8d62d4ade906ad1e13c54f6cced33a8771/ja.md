```
outcome_model(stochasticprogram::StochasticProgram{N},
              decisions::NTuple{N-1,AbstractVector}
              scenario_path::NTuple{N-1,AbstractScenario},
              optimizer = nothing)
```

`decisions`が前のステージで取られた決定であり、`scenario_path`が`stochasticprogram`のステージ`N`までの実現したシナリオである場合、結果の`N`:番目のステージモデルを返します。オプションで、結果モデルに適切な`solver`を供給してください。
