```
simulate_qiskit_ensemble(d_rand::RandDesign, qiskit_ensemble::Py, experiment_shots::Integer; backend::String = "qiskit", prefix::String = "result", simulator::Py = aer.AerSimulator(; method = "stabilizer"), diagnostics::Bool = true)
```

Qiskitを使用してランダム化された実験デザイン`d_rand`のシミュレーションデータを保存します。これは、[`get_stim_qiskit_ensemble`](@ref)によって生成されたQiskit回路のアンサンブル`qiskit_ensemble`に関連付けられ、各回路に対して`experiment_shots`ショットが行われます。保存されたデータは、提供された`backend`と`prefix`に従ってラベル付けされ、提供された`simulator`を使用してシミュレーションされ、`diagnostics`が`true`の場合は診断情報が表示されます。
