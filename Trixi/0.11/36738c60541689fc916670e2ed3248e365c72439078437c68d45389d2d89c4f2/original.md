```
flux_godunov(u_ll, u_rr, orientation_or_normal_direction,
             equations::LinearizedEulerEquations2D)
```

An upwind flux for the linearized Euler equations based on diagonalization of the physical flux matrix. Given the physical flux $Au$, $A=T \Lambda T^{-1}$ with $\Lambda$ being a diagonal matrix that holds the eigenvalues of $A$, decompose $\Lambda = \Lambda^+ + \Lambda^-$ where $\Lambda^+$ and $\Lambda^-$ are diagonal matrices holding the positive and negative eigenvalues of $A$, respectively. Then for left and right states $u_L, u_R$, the numerical flux calculated by this function is given by $A^+ u_L + A^- u_R$ where $A^{\pm} = T \Lambda^{\pm} T^{-1}$.

The diagonalization of the flux matrix can be found in

  * R. F. Warming, Richard M. Beam and B. J. Hyett (1975) Diagonalization and simultaneous symmetrization of the gas-dynamic matrices [DOI: 10.1090/S0025-5718-1975-0388967-5](https://doi.org/10.1090/S0025-5718-1975-0388967-5)
