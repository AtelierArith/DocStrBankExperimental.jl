```
rayleigh_replica_estimator(
    op_ol, vec_ol, shift, h, time_step;
    skip = 0,
    E_r = mean(shift[skip+1:end]),
    weights = w_exp,
    kwargs...
)
rayleigh_replica_estimator(
    df::DataFrame;
    shift_name="shift",
    op_name="Op1",
    vec_name="dot",
    h=0,
    skip=0,
    Anorm=1,
    kwargs...
)
rayleigh_replica_estimator(sim::PMCSimulation; kwargs...)
-> r::RatioBlockingResult
```

演算子 $\hat{A}$ のレイリー商の推定量を再重み付けを用いて計算します。

$$
A_\mathrm{est}(h) = \frac{\sum_{a<b} \sum_n w_{h,a}^{(n)} w_{h,b}^{(n)}
    \mathbf{c}_a^{(n)} \cdot \hat{A} \cdot \mathbf{c}_b^{(n)}}
    {\sum_{a<b} \sum_n w_{h,a}^{(n)} w_{h,b}^{(n)} \mathbf{c}_a^{(n)} \cdot \mathbf{c}_b^{(n)}},
$$

複数のレプリカからのデータを使用します。

引数 `op_ol` は演算子オーバーラップ $\mathbf{c}_a^{(n)} \hat{A} \mathbf{c}_b^{(n)}$ のデータを保持し、`vec_ol` はベクトルオーバーラップ $\mathbf{c}_a^{(n)} \mathbf{c}_b^{(n)}$ のデータを保持します。これらは `Vector{Vector}` 型であり、各要素 `Vector` はペアのレプリカのデータを保持します。引数 `shift` は `Vector{Vector}` 型であり、各要素 `Vector` は各個別レプリカのシフトデータを保持します。

2番目のメソッドは、`DataFrame` または [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) を返す [`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)) から直接レイリー商を計算します。キーワード引数 `shift_name`、`op_name`、`vec_name` を使用して関連する列の名前を変更できます。デフォルトのフォーマットについては [`AllOverlaps`](@ref Main.AllOverlaps) を参照してください。演算子オーバーラップデータは、前因子 `Anorm` によってスケーリングできます。特定の再重み付けの深さはキーワード引数 `h` で設定できます。デフォルトは `h = 0` で、再重み付けなしでレイリー商を計算します。

再重み付けは、[Umrigar *et al.* (1993)](http://dx.doi.org/10.1063/1.465195) で説明されている再重み付け技術を使用した混合推定量の拡張です。再重み付けは `h` タイムステップにわたって行われ、`length(shift) - skip` タイムステップが [`ratio_of_means`](@ref) で行われるブロッキング分析に使用されます。`weights` は重みを計算する関数です。[`w_exp`](@ref) および [`w_lin`](@ref) を参照してください。追加のキーワード引数は [`ratio_of_means`](@ref) に渡されます。

誤差伝播は [`MonteCarloMeasurements`](https://github.com/baggepinnen/MonteCarloMeasurements.jl) を使用して行われます。結果は [`RatioBlockingResult`](@ref) として返されます。

また、[`mixed_estimator`](@ref)、[`growth_estimator`](@ref) も参照してください。
