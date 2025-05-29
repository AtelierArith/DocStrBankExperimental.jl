```
DensityDiffusionMolteniColagrossi(; delta)
```

The commonly used density diffusion term by [Molteni (2009)](@cite Molteni2009).

The term $\psi_{ab}$ in the continuity equation in [`DensityDiffusion`](@ref) is defined by

$$
\psi_{ab} = 2(\rho_a - \rho_b) \frac{r_{ab}}{\Vert r_{ab} \Vert^2},
$$

where $\rho_a$ and $\rho_b$ denote the densities of particles $a$ and $b$ respectively and $r_{ab} = r_a - r_b$ is the difference of the coordinates of particles $a$ and $b$.

See [`DensityDiffusion`](@ref) for an overview and comparison of implemented density diffusion terms.
