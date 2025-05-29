```
LinearElastic
```

Linear elastic constitutive model that can be specified when using a [`CMaterial`](@ref) and [`BACMaterial`](@ref). The first Piola-Kirchhoff stress $\boldsymbol{P}$ is given by

$$
\boldsymbol{P} = \mathbb{C} : \boldsymbol{E} \; ,
$$

with the elastic stiffness tensor  $\mathbb{C}$ and the Green-Lagrange strain tensor $\boldsymbol{E}$ with

$$
\boldsymbol{E} = \frac{1}{2} \left( \boldsymbol{F}^{\top} \boldsymbol{F} - \boldsymbol{I}
                             \right) \; .
$$
