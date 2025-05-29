```
enstrophy(u, gradients, equations::CompressibleNavierStokesDiffusion2D)
```

Computes the (node-wise) enstrophy, defined as

$$
    \mathcal{E} = \frac{1}{2} \rho \omega \cdot \omega
$$

where $\omega = \nabla \times \boldsymbol{v}$ is the [`vorticity`](@ref). In 2D, $\omega$ is just a scalar.
