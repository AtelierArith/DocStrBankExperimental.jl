```
get_relative_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}}, gate_data::GateData)
```

ゲート確率 `gate_probabilities` から、各ゲートの軌道にわたるエラー確率を周辺化することによって得られる周辺ゲート確率を返します。これらのゲートは相対精度で推定可能です。
