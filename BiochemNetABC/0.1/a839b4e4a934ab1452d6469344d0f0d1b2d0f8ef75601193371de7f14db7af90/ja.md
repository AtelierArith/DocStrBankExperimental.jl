```
abc_smc(pm::ParametricModel, l_obs, func_dist; nbr_particles, alpha, kernel_type, NT
        duration_time, bound_sim, sym_var_aut, verbose)
```

pmパラメトリックモデルを使用してABC-SMCアルゴリズムを実行します。

`func_dist(l_sim, l_obs)`はシミュレーションと観測の間の距離関数であり、$\rho(\eta(y_sim), \eta(y_exp))\$に対応します。`l_obs::Vector{<:T2}`は観測のコレクションです。`dist`は`func_dist(l_sim::Vector{T1}, l_obs::Vector{T2})`の形式のシグネチャを持つ必要があります。

`pm`が`ContinuousTimeModel`上で定義されている場合、`T1`は`T1 <: Trajectory`を満たす必要があります。

!!! 距離関数と分散ABC     `abc_smc`を複数のワーカーで使用する場合、`dist`は@everywhereを使用してすべてのワーカーで定義する必要があります。
