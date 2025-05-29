```
𝒥(spinorbit1::Spinorbit, spinorbit2::Spinorbit, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

The *direct* integral of the electrostatic repulsion energy between two electrons in the (reduced) eigenstates `P1` and `P2` of an atom,  which correspond to the orbitals `orbit1` and `orbit2`.

$$
\mathcal{J}(u_{\kappa},u_{\kappa^{\prime}})=(u_{\kappa},u_{\kappa^{\prime}}|\frac{1}{\rho_{12}}|u_{\kappa},u_{\kappa^{\prime}})
=\int_{0}^{\infty}U_{F}(u_{\kappa},u_{\kappa^{\prime}};\rho)\left[\tilde{R}_{n^{\prime}l^{\prime}}(\rho)\right]^{2}\!\rho^{2}d\rho.
$$
