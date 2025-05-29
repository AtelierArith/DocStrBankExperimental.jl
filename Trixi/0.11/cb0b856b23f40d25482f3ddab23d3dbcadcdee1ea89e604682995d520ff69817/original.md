```
enstrophy(u, gradients, equations::CompressibleNavierStokesDiffusion3D)
```

Computes the (node-wise) enstrophy, defined as

$$
    \mathcal{E} = \frac{1}{2} \rho \boldsymbol{\omega} \cdot \boldsymbol{\omega}
$$

where $\boldsymbol{\omega} = \nabla \times \boldsymbol{v}$ is the [`vorticity`](@ref). In 3D, $\boldsymbol{\omega}$ is a full three-component vector.
