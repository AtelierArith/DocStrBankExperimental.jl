```
MooneyRivlin
```

Mooney-Rivlin constitutive model that can be specified when using a [`CMaterial`](@ref) and [`BACMaterial`](@ref). The first Piola-Kirchhoff stress $\boldsymbol{P}$ is given by

$$
\begin{aligned}
\boldsymbol{C} &= \boldsymbol{F}^{\top} \boldsymbol{F} \; , \\
\boldsymbol{S} &= G \left( \boldsymbol{I} - \frac{1}{3} \mathrm{tr}(\boldsymbol{C})
                           \boldsymbol{C}^{-1} \right) \cdot J^{-\frac{2}{3}}
                + \frac{K}{4} \left( J^2 - J^{-2} \right) \boldsymbol{C}^{-1} \; , \\
\boldsymbol{P} &= \boldsymbol{F} \, \boldsymbol{S} \; ,
\end{aligned}
$$

with the deformation gradient $\boldsymbol{F}$, the right Cauchy-Green deformation tensor $\boldsymbol{C}$, the Jacobian $J = \mathrm{det}(\boldsymbol{F})$, the second Piola-Kirchhoff stress $\boldsymbol{S}$, the shear modulus $G$, and the bulk modulus $K$.

# Error handling

If the Jacobian $J$ is smaller than the machine precision `eps()` or a `NaN`, the first Piola-Kirchhoff stress tensor is defined as $\boldsymbol{P} = \boldsymbol{0}$.
