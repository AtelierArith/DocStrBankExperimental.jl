```julia
etaFunction(psi, phi, UT, E, z) -> Any

```

The argument of the statistics function for given $\varphi_\alpha$ and $\psi$

$z_\alpha / U_T  ( (\varphi_\alpha - \psi) + E_\alpha / q ).$

The parameters $E_\alpha$ and $z_\alpha$ are given as vectors. This function may be used to compute the charge density, i.e. the right-hand side of the Poisson equation.
