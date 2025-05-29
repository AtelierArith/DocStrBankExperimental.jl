```
DissipationLaxFriedrichsEntropyVariables(max_abs_speed=max_abs_speed_naive)
```

Create a local Lax-Friedrichs-type dissipation operator that is provably entropy stable. This operator must be used together with an entropy-conservative two-point flux function (e.g., `flux_ec`) to yield  an entropy-stable surface flux. The surface flux function can be initialized as:

```julia
flux_es = FluxPlusDissipation(flux_ec, DissipationLaxFriedrichsEntropyVariables())
```

In particular, the numerical flux has the form

$$
f^{\mathrm{ES}} = f^{\mathrm{EC}} - \frac{1}{2} \lambda_{\mathrm{max}} H (w_r - w_l),
$$

where $f^{\mathrm{EC}}$ is the entropy-conservative two-point flux function (computed with, e.g., `flux_ec`), $\lambda_{\mathrm{max}}$  is the maximum wave speed estimated as `max_abs_speed(u_l, u_r, orientation_or_normal_direction, equations)`, defaulting to [`max_abs_speed_naive`](@ref), $H$ is a symmetric positive-definite dissipation matrix that depends on the left and right states `u_l` and `u_r`, and $(w_r - w_l)$ is the jump in entropy variables. Ideally, $H (w_r - w_l) = (u_r - u_l)$, such that the dissipation operator is consistent with the local Lax-Friedrichs dissipation.

The entropy-stable dissipation operator is computed with the function `function (dissipation::DissipationLaxFriedrichsEntropyVariables)(u_l, u_r, orientation_or_normal_direction, equations)`, which must be specialized for each equation.

For the derivation of the dissipation matrix for the multi-ion GLM-MHD equations, see:

  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).
