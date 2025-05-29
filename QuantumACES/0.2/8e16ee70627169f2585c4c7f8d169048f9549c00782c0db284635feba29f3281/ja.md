```
get_full_average_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}})
get_full_average_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}}, gate_data::GateData)
```

ゲート確率 `gate_probabilities` から得られた完全に平均化されたゲート確率を返します。これは、各ゲート内のすべてのエラー確率を平均化することによって得られます。
