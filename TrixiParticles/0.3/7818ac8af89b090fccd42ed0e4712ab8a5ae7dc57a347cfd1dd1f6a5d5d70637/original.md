```
DensityDiffusionFerrari()
```

A density diffusion term by [Ferrari (2009)](@cite Ferrari2009).

The term $\psi_{ab}$ in the continuity equation in [`DensityDiffusion`](@ref) is defined by

$$
\psi_{ab} = \frac{\rho_a - \rho_b}{h_a + h_b} \frac{r_{ab}}{\Vert r_{ab} \Vert},
$$

where $\rho_a$ and $\rho_b$ denote the densities of particles $a$ and $b$ respectively, $r_{ab} = r_a - r_b$ is the difference of the coordinates of particles $a$ and $b$ and $h_a$ and $h_b$ are the smoothing lengths of particles $a$ and $b$ respectively.

See [`DensityDiffusion`](@ref) for an overview and comparison of implemented density diffusion terms.
