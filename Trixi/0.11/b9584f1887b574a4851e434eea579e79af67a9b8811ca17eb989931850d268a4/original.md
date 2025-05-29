```
source_terms_collision_ion_ion(u, x, t,
                               equations::AbstractIdealGlmMhdMultiIonEquations)
```

Compute the ion-ion collision source terms for the momentum and energy equations of each ion species as

$$
\begin{aligned}
  \vec{s}_{\rho_k \vec{v}_k} =&  \rho_k\sum_{l}\bar{\nu}_{kl}(\vec{v}_{l} - \vec{v}_k),\\
  s_{E_k}  =& 
    3 \sum_{l} \left(
    \bar{\nu}_{kl} \frac{\rho_k M_1}{M_{l} + M_k} R_1 (T_{l} - T_k)
    \right) + 
    \sum_{l} \left(
        \bar{\nu}_{kl} \rho_k \frac{M_{l}}{M_{l} + M_k} \|\vec{v}_{l} - \vec{v}_k\|^2
        \right)
        +
        \vec{v}_k \cdot \vec{s}_{\rho_k \vec{v}_k},
\end{aligned}
$$

where $M_k$ is the molar mass of ion species `k` provided in `equations.molar_masses`,  $R_k$ is the specific gas constant of ion species `k` provided in `equations.gas_constants`, and  $\bar{\nu}_{kl}$ is the effective collision frequency of species `k` with species `l`, which is computed as

$$
\begin{aligned}
  \bar{\nu}_{kl} = \bar{\nu}^1_{kl} \tilde{B}_{kl} \frac{\rho_{l}}{T_{k l}^{3/2}},
\end{aligned}
$$

with the so-called reduced temperature $T_{k l}$ and the ion-ion collision constants $\tilde{B}_{kl}$ provided in `equations.ion_electron_collision_constants` (see [`IdealGlmMhdMultiIonEquations2D`](@ref)).

The additional coefficient $\bar{\nu}^1_{kl}$ is a non-dimensional drift correction factor proposed by Rambo and Denavit.

References:

  * P. Rambo, J. Denavit, Interpenetration and ion separation in colliding plasmas, Physics of Plasmas 1 (1994) 4050–4060. [DOI: 10.1063/1.870875](https://doi.org/10.1063/1.870875).
  * Schunk, R. W., Nagy, A. F. (2000). Ionospheres: Physics, plasma physics, and chemistry.  Cambridge university press. [DOI: 10.1017/CBO9780511635342](https://doi.org/10.1017/CBO9780511635342).
