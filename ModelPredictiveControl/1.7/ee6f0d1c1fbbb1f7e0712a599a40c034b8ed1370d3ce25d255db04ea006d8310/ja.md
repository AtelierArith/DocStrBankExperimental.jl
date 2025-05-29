```
MovingHorizonEstimator(
    model, He, i_ym, nint_u, nint_ym, P̂_0, Q̂, R̂, Cwt=Inf;
    optim=default_optim_mhe(model), 
    gradient=AutoForwardDiff(),
    jacobian=AutoForwardDiff(),
    direct=true,
    covestim=default_covestim_mhe(model, i_ym, nint_u, nint_ym, P̂_0, Q̂, R̂; direct)
)
```

拡張共分散行列 `P̂_0`、`Q̂` および `R̂` から推定器を構築します。

この構文では、非ゼロの非対角要素を持つことができ、$\mathbf{P̂_i}, \mathbf{Q̂, R̂}$ の要素を含むことができます。ここで、$\mathbf{P̂_i}$ は `P̂_0` 引数によって提供される初期推定共分散です。キーワード引数 `covestim` は、到着時の共分散の推定のためにカスタム [`StateEstimator`](@ref) オブジェクトを指定することも可能です。サポートされているタイプは [`KalmanFilter`](@ref)、[`UnscentedKalmanFilter`](@ref) および [`ExtendedKalmanFilter`](@ref) です。
