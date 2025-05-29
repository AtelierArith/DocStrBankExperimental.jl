```
mixed_estimator(
    hproj, vproj, shift, h, time_step;
    skip = 0,
    E_r = mean(shift[skip+1:end]),
    weights = w_exp,
    kwargs...
)
mixed_estimator(
    df::DataFrame, h;
    hproj_name=:hproj,
    vproj_name=:vproj,
    shift_name=:shift,
    time_step=determine_constant_time_step(df),
    kwargs...
)
mixed_estimator(sim::PMCSimulation, h; kwargs...)
-> r::RatioBlockingResult
```

[Umrigar *et al.* (1993)](http://dx.doi.org/10.1063/1.465195)で説明されている再重み付け技術を用いて混合推定量を計算します。式 (19)

$$
E_\mathrm{mix} = \frac{\sum_n w_{h}^{(n)}  (Ĥ'\mathbf{v})⋅\mathbf{c}^{(n)}}
        {\sum_m w_{h}^{(m)}  \mathbf{v}⋅\mathbf{c}^{(m)}} ,
$$

ここで、時系列 `hproj ==` $(Ĥ'\mathbf{v})⋅\mathbf{c}^{(n)}$ および `vproj ==` $\mathbf{v}⋅\mathbf{c}^{(m)}$ は `shift` と同じ長さを持ちます（これらの設定方法については [`ProjectedEnergy`](@ref Main.ProjectedEnergy) を参照してください）。再重み付けは `h` 時間ステップにわたって行われ、`length(shift) - skip` 時間ステップが [`ratio_of_means`](@ref) で行われるブロッキング分析に使用されます。`weights` は重みを計算する関数です。[`w_exp`](@ref) および [`w_lin`](@ref) を参照してください。追加のキーワード引数は [`ratio_of_means`](@ref) に渡されます。

`h` が `shift` の自己相関時間スケールより大きい場合、`r.ratio` は基底状態エネルギー $E_0$ のバイアスのない近似推定量であり、誤差は $\mathcal{O}(dτ^2)$ で、ここで $dτ$ は `time_step` であり、重み付けされていない比率と比較して信頼区間が潜在的に広がる可能性があります。誤差伝播は [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) を使用して行われます。結果は [`RatioBlockingResult`](@ref) として返されます。

第二の方法は、[`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)) によって返される `DataFrame` または [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) から直接混合エネルギー推定量を計算します。キーワード引数 `hproj_name`、`vproj_name`、および `shift_name` を使用して、関連する列の名前を変更できます。

[`growth_estimator`](@ref) も参照してください。
