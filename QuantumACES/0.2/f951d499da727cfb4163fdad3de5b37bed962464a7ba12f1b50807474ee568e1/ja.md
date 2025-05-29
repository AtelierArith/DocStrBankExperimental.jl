```
simulate_stim_ensemble(d_rand::RandDesign, stim_ensemble::Vector{Vector{String}}, experiment_shots::Integer; seed::Union{UInt64, Nothing} = nothing, diagnostics::Bool = true)
```

ランダム化された実験デザイン `d_rand` に対して、[`get_stim_qiskit_ensemble`](@ref) によって生成された関連するStim回路のアンサンブル `stim_ensemble` を使用して、Stimでシミュレートされたデータを保存します。各回路には `experiment_shots` ショットが含まれます。シミュレーションはランダムシード `seed` を使用し、`diagnostics` が `true` の場合は診断情報を表示します。
