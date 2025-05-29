```
estimate_stim_ensemble(d_rand::RandDesign, experiment_shots::Integer; fail_jobs::Vector{Int} = Int[], simulation_seed::Union{UInt64, Nothing} = nothing, ls_type::Symbol = :fgls, split::Bool = false, min_eigenvalue::Real = 0.1)
```

ランダム化された実験デザイン `d_rand` に対して、`experiment_shots` ショットごとに生成されたシミュレートされた Stim データから推定された回路の固有値とゲートノイズの推定値を返します。`fail_jobs` で指定された失敗したジョブの読み込みを試みることを避けます。シミュレートされたデータは、提供された `simulation_seed` によって暗示されるラベルに従って読み込まれ、推定手順は最小二乗推定器 `ls_type` を使用し、`split` が `true` の場合はゲートごとにゲート固有値推定器の射影を分割し、`min_eigenvalue` 以上の回路固有値のみを含みます。
