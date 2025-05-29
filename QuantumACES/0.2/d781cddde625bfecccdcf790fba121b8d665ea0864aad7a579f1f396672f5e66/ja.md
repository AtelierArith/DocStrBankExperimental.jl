```
get_average_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}})
get_average_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}}, gate_data::GateData)
```

ゲート確率 `gate_probabilities` から得られた平均ゲート確率を返します。これは、各ゲートの軌道内のエラー確率を平均化することによって得られます。
