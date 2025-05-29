```
min_max_speed_naive(u_ll, u_rr, orientation::Integer, equations)
min_max_speed_naive(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

左状態 `u_ll` と右状態 `u_rr` のリーマン問題の最小および最大波速の単純で迅速な推定(!)。通常、`u_ll` と `u_rr` に関連する局所波速のみに基づいています。[`min_max_speed_davis`](@ref) よりもわずかに拡散的です。

  * Amiram Harten, Peter D. Lax, Bram van Leer (1983) On Upstream Differencing and Godunov-Type Schemes for Hyperbolic Conservation Laws [DOI: 10.1137/1025002](https://doi.org/10.1137/1025002)

次の文献の eq. (10.37) を参照してください。

  * Eleuterio F. Toro (2009) Riemann Solvers and Numerical Methods for Fluid Dynamics: A Practical Introduction [DOI: 10.1007/b79761](https://doi.org/10.1007/b79761)

また、[`FluxHLL`](@ref)、[`min_max_speed_davis`](@ref)、[`min_max_speed_einfeldt`](@ref) も参照してください。
