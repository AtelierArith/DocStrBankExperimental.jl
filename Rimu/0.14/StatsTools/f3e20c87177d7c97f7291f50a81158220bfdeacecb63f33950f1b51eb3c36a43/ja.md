```
growth_estimator(
    shift, wn, h, time_step;
    skip = 0,
    E_r = mean(shift[skip+1:end]),
    weights = w_exp,
    change_type = identity,
    kwargs...
)
growth_estimator(
    df::DataFrame, h;
    shift_name=:shift,
    norm_name=:norm,
    time_step=determine_constant_time_step(df),
    kwargs...
)
growth_estimator(sim::PMCSimulation; kwargs...)
-> r::RatioBlockingResult
```

参照エネルギー `E_r` を用いて成長推定量を計算します。これは [Umrigar *et al.* (1993)](http://dx.doi.org/10.1063/1.465195) で説明されている再重み付け技術によるもので、式 (20) を参照してください。`shift` と `wn` はそれぞれシフトとウォーカーナンバーの時系列を含む同じ長さのベクトルです。再重み付けは `h` 時間ステップにわたって行われ、`length(shift) - skip` 時間ステップが [`ratio_of_means`](@ref) を用いたブロッキング分析に使用されます。`weights` は重みを計算する関数です。 [`w_exp`](@ref) と [`w_lin`](@ref) を参照してください。

$$
E_{gr} = E_r - \frac{1}{dτ}\ln
    \frac{\sum_n w_{h+1}^{(n+1)} N_\mathrm{w}^{(n+1)}}
        {\sum_m w_{h}^{(m)} N_\mathrm{w}^{(m)}} ,
$$

ここで $dτ$ は `time_step` です。

`h` が `shift` の自己相関時間スケールより大きい場合、`E_gr`（`r.ratio` として返される）は、基底状態エネルギー $E_0$ のバイアスのないが近似的な推定量であり、誤差は $\mathcal{O}(dτ^2)$ で、（バイアスのある）シフト推定量と比較して信頼区間が潜在的に増加します。誤差伝播は [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) を用いて行われます。負の外れ値からの `NaN` 結果を避けるために、`change_type` を [`to_measurement`](@ref) に設定することで対数を通じた伝播を修正できます。

`success==true` の場合、ブロッキング分析は `k-1` ステップで成功し、`blocks` の非相関データポイントを使用しました。

第二の方法は、[`PMCSimulation`](@ref Main.Rimu.PMCSimulation) または [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)) によって返される `DataFrame` から直接成長推定量を計算します。キーワード引数 `shift_name` と `norm_name` を使用して、関連する列の名前を変更できます。

[`mixed_estimator`](@ref) と [`RatioBlockingResult`](@ref) も参照してください。
