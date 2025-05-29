```
simulate_stim_estimate(d::Design, shots_set::Vector{Int}; kwargs...)
```

実験デザイン `d` に対して、`shots_set` の各測定ショットにわたるシミュレーションされた推定回路固有値、共分散回路固有値、および対応する回路固有値ペアを返します。

# キーワード引数

  * `seed::Union{UInt64, Nothing} = nothing`: Stim のランダムシードを制御するシード。
  * `max_samples::Integer = 10^9`: 単一の Stim シミュレーションで取得する最大サンプル数。
  * `detailed_diagnostics::Bool = false`: シミュレーションに関する診断情報を印刷するかどうか。
