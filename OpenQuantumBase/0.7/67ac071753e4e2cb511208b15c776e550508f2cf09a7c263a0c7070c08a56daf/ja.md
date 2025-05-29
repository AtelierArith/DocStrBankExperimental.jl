```julia
coarse_grain_timescale(bath, lim; rtol, atol)

```

最適な粗粒子時間スケール $T_a=√{τ_{SB}τ_B/5}$ を総進化時間 `lim` に対して計算します。`atol` と `rtol` は積分の絶対誤差と相対誤差です。
