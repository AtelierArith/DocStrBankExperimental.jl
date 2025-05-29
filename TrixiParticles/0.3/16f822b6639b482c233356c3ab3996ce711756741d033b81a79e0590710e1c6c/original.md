```
DensityDiffusionAntuono(initial_condition; delta)
```

The commonly used density diffusion terms by [Antuono (2010)](@cite Antuono2010), also referred to as δ-SPH. The density diffusion term by [Molteni (2009)](@cite Molteni2009) is extended by a second term, which is nicely written down by [Antuono (2012)](@cite Antuono2012).

The term $\psi_{ab}$ in the continuity equation in [`DensityDiffusion`](@ref) is defined by

$$
\psi_{ab} = 2\left(\rho_a - \rho_b - \frac{1}{2}\big(\nabla\rho^L_a + \nabla\rho^L_b\big) \cdot r_{ab}\right)
    \frac{r_{ab}}{\Vert r_{ab} \Vert^2},
$$

where $\rho_a$ and $\rho_b$ denote the densities of particles $a$ and $b$ respectively and $r_{ab} = r_a - r_b$ is the difference of the coordinates of particles $a$ and $b$. The symbol $\nabla\rho^L_a$ denotes the renormalized density gradient defined as

$$
\nabla\rho^L_a = -\sum_b (\rho_a - \rho_b) V_b L_a \nabla_{r_a} W(\Vert r_{ab} \Vert, h)
$$

with

$$
L_a := \left( -\sum_{b} V_b r_{ab} \otimes \nabla_{r_a} W(\Vert r_{ab} \Vert, h) \right)^{-1} \in \R^{d \times d},
$$

where $d$ is the number of dimensions.

See [`DensityDiffusion`](@ref) for an overview and comparison of implemented density diffusion terms.
