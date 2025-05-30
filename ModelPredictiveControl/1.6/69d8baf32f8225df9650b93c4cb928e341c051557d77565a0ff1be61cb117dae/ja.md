```
ExtendedKalmanFilter(
    model, i_ym, nint_u, nint_ym, P̂_0, Q̂, R̂; jacobian=AutoForwardDiff(), direct=true
)
```

拡張カルマンフィルタを、拡張共分散行列 `P̂_0`、`Q̂` および `R̂` から構築します。

この構文は、$\mathbf{P̂}_{-1}(0), \mathbf{Q̂, R̂}$ の非ゼロのオフ対角要素を許可します。
