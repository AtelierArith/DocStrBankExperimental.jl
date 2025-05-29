```
FluxHLL(min_max_speed=min_max_speed_davis)
```

HLL（Harten, Lax, van Leer）数値フラックスを作成します。最小および最大波速度は `λ_min, λ_max = min_max_speed(u_ll, u_rr, orientation_or_normal_direction, equations)` として推定され、デフォルトは [`min_max_speed_davis`](@ref) です。元の論文：

  * Amiram Harten, Peter D. Lax, Bram van Leer (1983) On Upstream Differencing and Godunov-Type Schemes for Hyperbolic Conservation Laws [DOI: 10.1137/1025002](https://doi.org/10.1137/1025002)
