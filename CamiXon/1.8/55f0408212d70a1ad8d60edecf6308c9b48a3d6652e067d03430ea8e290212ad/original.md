```
UG(spinorbit1::Spinorbit, spinorbit2::Spinorbit, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

Potential of *exchange* screening of two electrons with (reduced) wavefunctions `P1` and `P2`, corresponding to the electronic orbitals `orbit1` and `orbit2`.

NB.  `UG(spinorbit1, spinorbit2, P1, P2, grid)` = `UG(spinorbit2, spinorbit1, P1, P2, grid)`

$$
U_{G}(u_{\kappa},u_{\kappa^{\prime}};\rho)
={\textstyle \sum\limits_{k=0}^{\infty}}b^{k}(lm_{l};l^{\prime}m_{l^{\prime}})U_{G}^{k}(nl,n^{\prime}l^{\prime};\rho).
$$

#### Example:

```

```
