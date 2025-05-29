```
get_stim_qiskit_ensemble(d_rand::RandDesign, qiskit_qubit_num::Integer, qiskit_qubit_map::Vector{Int})
```

ランダム化されたアンサンブル `d_rand` のためのStimおよびQiskit回路を返します。

Qiskit回路は `qiskit_qubit_num` 個のキュービットに作用し、一般的には `maximum(qiskit_qubit_map) + 1` 以上でなければなりません。また、回路が作用するキュービットのマッピングは `qiskit_qubit_map` によって制御され、これは回路が作用するキュービットの数と同じ長さのベクトルです。
