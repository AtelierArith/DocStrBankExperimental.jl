```
SteadyKalmanFilter(model, i_ym, nint_u, nint_ym, Q̂, R̂; direct=true)
```

拡張共分散行列 `Q̂` と `R̂` から推定器を構築します。

この構文は、$\mathbf{Q̂, R̂}$ の非ゼロのオフ対角要素を許可します。
