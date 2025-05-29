```
get_marginal_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}})
get_marginal_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}}, gate_data::GateData)
```

ゲート確率 `gate_probabilities` から各ゲートの軌道にわたってエラー確率を周辺化することによって得られる周辺ゲート確率を返します。
