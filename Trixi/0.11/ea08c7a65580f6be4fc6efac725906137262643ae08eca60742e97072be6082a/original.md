```
source_terms_collision_ion_electron(u, x, t,
                                    equations::AbstractIdealGlmMhdMultiIonEquations)
```

Compute the ion-electron collision source terms for the momentum and energy equations of each ion species. We assume $v_e = v^+$  (no effect of currents on the electron velocity).

The collision sources read as

$$
\begin{aligned}
    \vec{s}_{\rho_k \vec{v}_k} =&  \rho_k \bar{\nu}_{ke} (\vec{v}_{e} - \vec{v}_k),
    \\
    s_{E_k}  =& 
    3  \left(
    \bar{\nu}_{ke} \frac{\rho_k M_{1}}{M_k} R_1 (T_{e} - T_k)
    \right) 
        +
        \vec{v}_k \cdot \vec{s}_{\rho_k \vec{v}_k},
\end{aligned}
$$

where $T_e$ is the electron temperature computed with the function `equations.electron_temperature`,  $M_k$ is the molar mass of ion species `k` provided in `equations.molar_masses`,  $R_k$ is the specific gas constant of ion species `k` provided in `equations.gas_constants`, and $\bar{\nu}_{ke}$ is the collision frequency of species `k` with the electrons, which is computed as

$$
\begin{aligned}
  \bar{\nu}_{ke} = \tilde{B}_{ke} \frac{e n_e}{T_e^{3/2}},
\end{aligned}
$$

with the total electron charge $e n_e$ (computed assuming quasi-neutrality), and the ion-electron collision coefficient $\tilde{B}_{ke}$ provided in `equations.ion_electron_collision_constants`, which is scaled with the elementary charge (see [`IdealGlmMhdMultiIonEquations2D`](@ref)).

References:

  * P. Rambo, J. Denavit, Interpenetration and ion separation in colliding plasmas, Physics of Plasmas 1 (1994) 4050–4060. [DOI: 10.1063/1.870875](https://doi.org/10.1063/1.870875).
  * Schunk, R. W., Nagy, A. F. (2000). Ionospheres: Physics, plasma physics, and chemistry.  Cambridge university press. [DOI: 10.1017/CBO9780511635342](https://doi.org/10.1017/CBO9780511635342).
