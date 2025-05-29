```
sysd, x0map = c2d_x0map(sys::AbstractStateSpace{<:Continuous}, Ts, method=:zoh; w_prewarp=0)
```

システム `sys` の離散化 `sysd` と、初期条件を離散領域に変換する行列 `x0map` を返します。これは `x0_discrete = x0map*[x0; u0]` によって行われます。

詳細については `c2d` を参照してください。
