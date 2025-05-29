```
UnscentedKalmanFilter(
    model, i_ym, nint_u, nint_ym, P̂_0, Q̂, R̂, α=1e-3, β=2, κ=0; direct=true
)
```

拡張共分散行列 `P̂_0`, `Q̂` および `R̂` から推定器を構築します。

この構文は、$\mathbf{P̂}_{-1}(0), \mathbf{Q̂, R̂}$ の非ゼロのオフ対角要素を許可します。
