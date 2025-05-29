```
get_stim_memory_circuit(c::AbstractCircuit, gate_probabilities::Dict{Gate, Vector{Float64}}, memory_type::Symbol, rounds::Integer; reset_type::Symbol = :meas_reset)
get_stim_memory_circuit(c::AbstractCircuit, memory_type::Symbol, rounds::Integer; reset_type::Symbol = :meas_reset)
```

`c`に対応するシンドローム抽出回路のメモリ回路のStim文字列表現を返します。オプションでゲートエラー確率`gate_probabilities`、メモリタイプ`memory_type`（`:x`または`:z`）、ラウンド数`rounds`、およびリセットタイプ`reset_type`（`:meas_reset`または`:meas`）を使用できます。

[`CodeParameters`](@ref)オブジェクトにコードパラメータを保存しないカスタムシンドローム抽出回路`c`をサポートする場合は、この関数が機能するように`get_stim_qubits`、`get_stim_initialise`、`get_stim_detectors`、および`get_stim_measure_detectors`の新しいメソッドを定義する必要があります。
