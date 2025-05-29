```
get_stim_circuit(c::AbstractCircuit)
get_stim_circuit(c::AbstractCircuit, circuit_tuple::Vector{Int})
get_stim_circuit(c::AbstractCircuit, gate_probabilities::Dict{Gate, Vector{Float64}})
get_stim_circuit(c::AbstractCircuit, circuit_tuple::Vector{Int}, gate_probabilities::Dict{Gate, Vector{Float64}})
get_stim_circuit(d::Design)
get_stim_circuit(d::Design, gate_probabilities::Dict{Gate, Vector{Float64}})
get_stim_circuit(d_rand::RandDesign)
get_stim_circuit(d_rand::RandDesign, gate_probabilities::Dict{Gate, Vector{Float64}})
```

回路 `c` のための Stim 回路を返し、設計 `d` またはランダム化設計 `d_rand` に格納され、オプションでゲート確率 `gate_probabilities` を持つタプル `circuit_tuple` を適用します。
