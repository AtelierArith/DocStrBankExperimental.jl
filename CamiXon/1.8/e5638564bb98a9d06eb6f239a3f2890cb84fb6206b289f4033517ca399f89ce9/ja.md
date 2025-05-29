```
𝒦(spinorbit1::Spinorbit, spinorbit2::Spinorbit, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

*交換* 積分

$$
\mathcal{K}(u_{\kappa},u_{\kappa^{\prime}})=(u_{\kappa},u_{\kappa^{\prime}}|\frac{1}{\rho_{12}}|u_{\kappa^{\prime}},u_{\kappa})
=\int_{0}^{\infty}U_{G}(u_{\kappa},u_{\kappa^{\prime}};\rho)\tilde{R}_{nl}(\rho)\tilde{R}_{n^{\prime}l^{\prime}}(\rho)\rho^{2}d\rho.
$$
