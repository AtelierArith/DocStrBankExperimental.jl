```
estimate_qiskit_ensemble(d_rand::RandDesign, qiskit_qubit_map::Vector{Int}, experiment_shots::Integer; fail_jobs::Vector{Int} = Int[], backend::String = "qiskit", ls_type::Symbol = :fgls, split::Bool = false, min_eigenvalue::Real = 0.1)
```

Qiskitデータを[`process_qiskit_ensemble`]で処理した結果から、ランダム化された実験デザイン`d_rand`に対して、各回路ごとに`experiment_shots`ショットの推定された回路固有値とゲートノイズの推定値を返します。`fail_jobs`で指定された失敗したジョブの読み込みを試みることを避けます。シミュレーションデータは、提供された`backend`によって示されるラベルに従って読み込まれ、推定手順は最小二乗推定器`ls_type`を使用し、`split`が`true`の場合はゲート固有値推定器の投影をゲート間で分割し、`min_eigenvalue`以上の回路固有値のみを含みます。
