```
𝒥(spinorbit1::Spinorbit, spinorbit2::Spinorbit, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

2つの電子間の静電反発エネルギーの*直接*積分であり、原子の軌道 `orbit1` と `orbit2` に対応する（縮約された）固有状態 `P1` と `P2` の間のものです。

$$
\mathcal{J}(u_{\kappa},u_{\kappa^{\prime}})=(u_{\kappa},u_{\kappa^{\prime}}|\frac{1}{\rho_{12}}|u_{\kappa},u_{\kappa^{\prime}})
=\int_{0}^{\infty}U_{F}(u_{\kappa},u_{\kappa^{\prime}};\rho)\left[\tilde{R}_{n^{\prime}l^{\prime}}(\rho)\right]^{2}\!\rho^{2}d\rho.
$$
