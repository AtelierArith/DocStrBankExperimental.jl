```
process_qiskit_ensemble(d_rand::RandDesign, qiskit_qubit_num::Integer, qiskit_qubit_map::Vector{Int}, experiment_shots::Integer; backend::String = "qiskit", prefix::String = "result")
```

ランダム化された実験デザイン `d_rand` の保存されたQiskitデータの処理されたバージョンを保存します。これは、例えば [`simulate_qiskit_ensemble`](@ref) によって生成され、関連するQiskit回路のアンサンブルが `qiskit_qubit_num` 個のキュービットに作用し、マッピング `qiskit_qubit_map` によってインデックス付けされ、各回路に対して `experiment_shots` ショットで実行されたものです。保存されたデータは、提供された `backend` と `prefix` によって暗示されるラベリングに従ってロードされます。
