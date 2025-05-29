```
NeoHooke
```

Neo-Hookean constitutive model that can be specified when using a [`CMaterial`](@ref) and [`BACMaterial`](@ref). The first Piola-Kirchhoff stress $\boldsymbol{P}$ is given by

$$
\begin{aligned}
\boldsymbol{C} &= \boldsymbol{F}^{\top} \boldsymbol{F} \; , \\
\boldsymbol{S} &= \mu \left( \boldsymbol{I} - \boldsymbol{C}^{-1} \right)
    + \lambda \log(J) \boldsymbol{C}^{-1} \; , \\
\boldsymbol{P} &= \boldsymbol{F} \, \boldsymbol{S} \; ,
\end{aligned}
$$

with the deformation gradient $\boldsymbol{F}$, the right Cauchy-Green deformation tensor $\boldsymbol{C}$, the Jacobian $J = \mathrm{det}(\boldsymbol{F})$, the second Piola-Kirchhoff stress $\boldsymbol{S}$, and the first and second Lamé parameters $\lambda$ and $\mu$.
