```
HOCartesianEnergyConservedPerDim(addr; S, η, g = 1.0, interaction_only = false)
```

Implements a bosonic harmonic oscillator in Cartesian basis with contact interactions

$$
\hat{H} = \sum_{i} ϵ_i n_i + \frac{g}{2}\sum_{ijkl} V_{ijkl} a^†_i a^†_j a_k a_l,
$$

with the additional restriction that the interactions only couple states with the same energy in each dimension separately. See [`HOCartesianContactInteractions`](@ref) for a model that conserves total energy.

For a $D$-dimensional harmonic oscillator indices $\mathbf{i}, \mathbf{j}, \ldots$ are $D$-tuples. The energy scale is defined by the first dimension i.e. $\hbar \omega_x$ so that single particle energies are

$$
    \frac{\epsilon_\mathbf{i}}{\hbar \omega_x} = (i_x + 1/2) + \eta_y (i_y+1/2) + \ldots.
$$

The factors $\eta_y, \ldots$ allow for anisotropic trapping geometries and are assumed to be greater than `1` so that $\omega_x$ is the smallest trapping frequency.

Matrix elements $V_{\mathbf{ijkl}}$ are for a contact interaction calculated in this basis using first-order degenerate perturbation theory.

$$
    V_{\mathbf{ijkl}} = \prod_{d \in x, y,\ldots} \mathcal{I}(i_d,j_d,k_d,l_d)
        \delta_{i_d + j_d}^{k_d + l_d},
$$

where the $\delta$-function indicates that the noninteracting energy is conserved along each dimension. The integral $\mathcal{I}(a,b,c,d)$ is of four one dimensional harmonic oscillator basis functions, see [`four_oscillator_integral_general`](@ref), with the additional restriction that energy is conserved in each dimension.

# Arguments

  * `addr`: the starting address, defines number of particles and total number of modes.
  * `S`: Tuple of the number of levels in each dimension, including the groundstate. Defaults   to a 1D spectrum with number of levels matching modes of `addr`. Will be sorted to   make the first dimension the largest.
  * `η`: Define a custom aspect ratio for the trapping potential strengths, instead of deriving   from `S .- 1`. The values are always scaled relative to the first dimension, which sets   the energy scale of the system, $\hbar\omega_x$.
  * `g`: the (isotropic) interparticle interaction parameter. The value of `g` is assumed   to be in trap units.
  * `interaction_only`: if set to `true` then the noninteracting single-particle terms are   ignored. Useful if only energy shifts due to interactions are required.
