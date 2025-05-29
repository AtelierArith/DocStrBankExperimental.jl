```
qec_merge(data...) -> Vector{Dict}
```

シミュレーション実行データをマージします。

実行データは[`qec_run`](@ref)で指定された形式であることが期待されます。マージされたデータは、`(:code, :n_k_d, :error_model, :decoder, :error_probability, :time_steps, :measurement_error_probability)`でグループ化されます。スカラー値`:n_run`、`:n_success`、`:n_fail`、`:error_weight_total`および`:wall_time`は合計されます。ベクトル値`:n_logical_commutations`は要素ごとに合計されます。ベクトル値`:custom_totals`はスカラー要素については要素ごとに合計され、配列要素については次元1に沿って連結されます（`vcat`）。値`:logical_failure_rate`および`:physical_error_rate`は再計算されます。値`:error_weight_pvar`は現在再計算されておらず、したがって省略されます。

# 例

```jldoctest; filter = r":wall_time +=> \d*\.?\d*"
julia> using Qecsim.BasicModels, Qecsim.GenericModels, Logging

julia> code, error_model, decoder = FiveQubitCode(), BitFlipErrorModel(), NaiveDecoder();

julia> data = Dict[];

julia> with_logger(NullLogger()) do # 簡潔さのためにログ記録を無効にする
           push!(data, qec_run(code, error_model, decoder, 0.08, 19; max_runs=100))
           push!(data, qec_run(code, error_model, decoder, 0.08, 23; max_runs=100))
       end;

julia> qec_merge(data...)
1-element Vector{Dict{Symbol, Any}}:
 Dict(:measurement_error_probability => 0.0, :error_probability => 0.08, :time_steps => 1, :error_weight_total => 83, :n_logical_commutations => [11, 3], :wall_time => 0.0028351720000000004, :n_k_d => (5, 1, 3), :error_model => "Bit-flip", :n_success => 189, :logical_failure_rate => 0.055…)
```
