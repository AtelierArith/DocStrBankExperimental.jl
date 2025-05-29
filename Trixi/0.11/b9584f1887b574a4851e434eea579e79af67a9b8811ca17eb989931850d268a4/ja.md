```
source_terms_collision_ion_ion(u, x, t,
                               equations::AbstractIdealGlmMhdMultiIonEquations)
```

各イオン種の運動量およびエネルギー方程式のためのイオン-イオン衝突ソース項を次のように計算します。

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

ここで、$M_k$は`equations.molar_masses`に提供されるイオン種`k`のモル質量、$R_k$は`equations.gas_constants`に提供されるイオン種`k`の特定ガス定数、$\bar{\nu}_{kl}$は種`k`と種`l`の有効衝突頻度であり、次のように計算されます。

$$
\begin{aligned}
  \bar{\nu}_{kl} = \bar{\nu}^1_{kl} \tilde{B}_{kl} \frac{\rho_{l}}{T_{k l}^{3/2}},
\end{aligned}
$$

いわゆる縮小温度$T_{k l}$とイオン-イオン衝突定数$\tilde{B}_{kl}$は`equations.ion_electron_collision_constants`に提供されています（[`IdealGlmMhdMultiIonEquations2D`](@ref)を参照）。

追加の係数$\bar{\nu}^1_{kl}$は、RamboとDenavitによって提案された無次元のドリフト補正因子です。

参考文献：

  * P. Rambo, J. Denavit, Interpenetration and ion separation in colliding plasmas, Physics of Plasmas 1 (1994) 4050–4060. [DOI: 10.1063/1.870875](https://doi.org/10.1063/1.870875).
  * Schunk, R. W., Nagy, A. F. (2000). Ionospheres: Physics, plasma physics, and chemistry.  Cambridge university press. [DOI: 10.1017/CBO9780511635342](https://doi.org/10.1017/CBO9780511635342).
