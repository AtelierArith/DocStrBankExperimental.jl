```
SaintVenantKirchhoff
```

Saint-Venant-Kirchhoff constitutive model that can be specified when using a [`CMaterial`](@ref) and [`BACMaterial`](@ref). The first Piola-Kirchhoff stress $\boldsymbol{P}$ is given by

$$
\begin{aligned}
\boldsymbol{E} &= \frac{1}{2} \left( \boldsymbol{F}^{\top} \boldsymbol{F} - \boldsymbol{I}
                              \right) \; , \\
\boldsymbol{S} &= \lambda \, \mathrm{tr}(\boldsymbol{E}) \, \boldsymbol{I}
                + 2 \mu \boldsymbol{E} \; , \\
\boldsymbol{P} &= \boldsymbol{F} \, \boldsymbol{S} \; ,
\end{aligned}
$$

with the deformation gradient $\boldsymbol{F}$, the Green-Lagrange strain tensor $\boldsymbol{E}$, the second Piola-Kirchhoff stress $\boldsymbol{S}$, and the first and second Lamé parameters $\lambda$ and $\mu$.
