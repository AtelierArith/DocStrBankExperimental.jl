```
ExplicitMPC(model::LinModel; <キーワード引数>)
```

[`LinModel`](@ref) `model`に基づいて明示的な線形予測制御器を構築します。

この制御器は、各離散時間$k$において以下の目的関数を最小化します：

$$
\begin{aligned}
\min_{\mathbf{ΔU}}   \mathbf{(R̂_y - Ŷ)}' \mathbf{M}_{H_p} \mathbf{(R̂_y - Ŷ)}     
                   + \mathbf{(ΔU)}'      \mathbf{N}_{H_c} \mathbf{(ΔU)}        \\
                   + \mathbf{(R̂_u - U)}' \mathbf{L}_{H_p} \mathbf{(R̂_u - U)} 
\end{aligned}
$$

変数の定義については[`LinMPC`](@ref)を参照してください。この制御器は制約をサポートしていませんが、計算コストは非常に低く（配列の除算）、したがって小さなサンプル時間を必要とするアプリケーションに適しています。キーワード引数は[`LinMPC`](@ref)と同じですが、`Cwt`と`optim`はサポートされていません。この制御器は[`SingleShooting`](@ref)転写法を使用します。

このメソッドは、デフォルトの状態推定器であるデフォルト引数を持つ[`SteadyKalmanFilter`](@ref)を使用します。この制御器はアロケーションフリーです。

# 例

```jldoctest
julia> model = LinModel([tf(3, [30, 1]); tf(-2, [5, 1])], 4);

julia> mpc = ExplicitMPC(model, Mwt=[0, 1], Nwt=[0.5], Hp=30, Hc=1)
ExplicitMPC controller with a sample time Ts = 4.0 s, SteadyKalmanFilter estimator and:
 30 prediction steps Hp
  1 control steps Hc
  1 manipulated inputs u (0 integrating states)
  4 estimated states x̂
  2 measured outputs ym (2 integrating states)
  0 unmeasured outputs yu
  0 measured disturbances d
```
