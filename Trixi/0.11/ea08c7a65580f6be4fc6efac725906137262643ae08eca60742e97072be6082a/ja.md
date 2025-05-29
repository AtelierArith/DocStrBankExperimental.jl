```
source_terms_collision_ion_electron(u, x, t,
                                    equations::AbstractIdealGlmMhdMultiIonEquations)
```

各イオン種の運動量およびエネルギー方程式のためのイオン-電子衝突ソース項を計算します。$v_e = v^+$（電子速度に対する電流の影響はない）と仮定します。

衝突ソースは次のように表されます。

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

ここで、$T_e$は関数`equations.electron_temperature`を用いて計算された電子温度、$M_k$は`equations.molar_masses`に提供されるイオン種`k`のモル質量、$R_k$は`equations.gas_constants`に提供されるイオン種`k`の特定ガス定数、$\bar{\nu}_{ke}$は電子とのイオン種`k`の衝突頻度であり、次のように計算されます。

$$
\begin{aligned}
  \bar{\nu}_{ke} = \tilde{B}_{ke} \frac{e n_e}{T_e^{3/2}},
\end{aligned}
$$

ここで、総電子電荷$e n_e$（準中性を仮定して計算）と、`equations.ion_electron_collision_constants`に提供されるイオン-電子衝突係数$\tilde{B}_{ke}$は、基本電荷でスケーリングされています（見よ [`IdealGlmMhdMultiIonEquations2D`](@ref)）。

参考文献：

  * P. Rambo, J. Denavit, Interpenetration and ion separation in colliding plasmas, Physics of Plasmas 1 (1994) 4050–4060. [DOI: 10.1063/1.870875](https://doi.org/10.1063/1.870875).
  * Schunk, R. W., Nagy, A. F. (2000). Ionospheres: Physics, plasma physics, and chemistry.  Cambridge university press. [DOI: 10.1017/CBO9780511635342](https://doi.org/10.1017/CBO9780511635342).
