```
HOCartesianContactInteractions(addr; S, η, g = 1.0, interaction_only = false, block_by_level = true)
```

Implements a bosonic harmonic oscillator in Cartesian basis with contact interactions

$$
\hat{H} = \sum_{i} \epsilon_\mathbf{i} n_\mathbf{i} + \frac{g}{2}\sum_\mathbf{ijkl}
    V_\mathbf{ijkl} a^†_\mathbf{i} a^†_\mathbf{j} a_\mathbf{k} a_\mathbf{l}.
$$

For a $D$-dimensional harmonic oscillator indices $\mathbf{i}, \mathbf{j}, \ldots$ are $D$-tuples. The energy scale is defined by the first dimension i.e. $\hbar \omega_x$ so that single particle energies are

$$
    \frac{\epsilon_\mathbf{i}}{\hbar \omega_x} = (i_x + 1/2) + \eta_y (i_y+1/2) + \ldots.
$$

The factors $\eta_y, \ldots$ allow for anisotropic trapping geometries and are assumed to be greater than `1` so that $\omega_x$ is the smallest trapping frequency.

By default the offdiagonal elements due to the interactions are consistent with first-order degenerate perturbation theory

$$
    V_{\mathbf{ijkl}} = \delta_{\epsilon_\mathbf{i} + \epsilon_\mathbf{j}}
        ^{\epsilon_\mathbf{k} + \epsilon_\mathbf{l}}
        \prod_{d \in x, y,\ldots} \mathcal{I}(i_d,j_d,k_d,l_d),
$$

where the $\delta$ function indicates that the *total* noninteracting energy is conserved meaning all states with the same noninteracting energy are connected by this interaction and the Hamiltonian blocks according to noninteracting energy levels. Setting `block_by_level = false` will disable this restriction and allow coupling between basis states of any noninteracting energy level, leading to many more offdiagonals and fewer but larger blocks (the blocks are still distinguished by parity of basis states). Alternatively, see [`HOCartesianEnergyConservedPerDim`](@ref) for a model with the stronger restriction that conserves energy separately per spatial dimension. The integral $\mathcal{I}(a,b,c,d)$ is of four one dimensional harmonic oscillator basis functions, implemented in [`four_oscillator_integral_general`](@ref).

# Arguments

  * `addr`: the starting address, defines number of particles and total number of modes.
  * `S`: Tuple of the number of levels in each dimension, including the groundstate. The   allowed couplings between states is defined by the aspect ratio of `S .- 1`. Defaults   to a 1D spectrum with number of levels matching modes of `addr`. Will be sorted to make   the first dimension the largest.
  * `η`: Define a custom aspect ratio for the trapping potential strengths, instead of deriving   from `S .- 1`. This will only affect the single particle energy scale and not the   interactions. The values are always scaled relative to the first dimension, which sets   the energy scale of the system, $\hbar\omega_x$.
  * `g`: the (isotropic) bare interaction parameter. The value of `g` is assumed   to be in trap units.
  * `interaction_only`: if set to `true` then the noninteracting single-particle terms are   ignored. Useful if only energy shifts due to interactions are required.
  * `block_by_level`: if set to false will allow the interactions to couple all states without   comparing their noninteracting energy.

!!! warning
    `num_offdiagonals` is a bad estimate for this Hamiltonian. Take care when building a matrix or using QMC methods. Use [`get_all_blocks`](@ref) first then pass option `col_hint = block_size` to [`BasisSetRep`](@ref) to safely build the matrix.

