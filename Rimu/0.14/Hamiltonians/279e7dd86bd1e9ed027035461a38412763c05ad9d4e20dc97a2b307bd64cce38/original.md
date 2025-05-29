```
HOCartesianCentralImpurity(addr; kwargs...)
```

Hamiltonian of non-interacting particles in an arbitrary harmonic trap with a delta-function potential at the centre, with strength `g`,

$$
\hat{H}_\mathrm{rel} = \sum_\mathbf{i} ϵ_\mathbf{i} n_\mathbf{i}
    + g\sum_\mathbf{ij} V_\mathbf{ij} a^†_\mathbf{i} a_\mathbf{j}.
$$

For a $D$-dimensional harmonic oscillator indices $\mathbf{i}, \mathbf{j}, \ldots$ are $D$-tuples. The energy scale is defined by the first dimension i.e. $\hbar \omega_x$ so that single particle energies are

$$
    \frac{\epsilon_\mathbf{i}}{\hbar \omega_x} = (i_x + 1/2) + \eta_y (i_y+1/2) + \ldots.
$$

The factors $\eta_y, \ldots$ allow for anisotropic trapping geometries and are assumed to be greater than `1` so that $\omega_x$ is the smallest trapping frequency.

Matrix elements $V_{\mathbf{ij}}$ are for a delta function potential calculated in this basis

$$
    V_{\mathbf{ij}} = \prod_{d \in x, y,\ldots} \psi_{i_d}(0) \psi_{j_d}(0).
$$

Only even parity states feel this impurity, so all $i_d$ are even. Note that the matrix representation of this Hamiltonian for a single particle is completely dense in the even-parity subspace.

# Arguments

  * `addr`: the starting address, defines number of particles and total number of modes.
  * `max_nx = num_modes(addr) - 1`: the maximum harmonic oscillator index number in the $x$-dimension.   Must be even. Index number for the harmonic oscillator groundstate is `0`.
  * `ηs = ()`: a tuple of aspect ratios for the remaining dimensions `(η_y, ...)`. Should be empty   for a 1D trap or contain values greater than `1.0`. The maximum index   in other dimensions will be the largest even number less than `M/η_y`.
  * `S = nothing`: Instead of `max_nx`, manually set the number of levels in each dimension,   including the groundstate. Must be a `Tuple` of `Int`s.
  * `g = 1.0`: the strength of the delta impurity in ($x$-dimension) trap units.
  * `impurity_only=false`: if set to `true` then the trap energy terms are ignored. Useful if   only energy shifts due to the impurity are required.

!!! warning
    ```
    Due to use of `SpecialFunctions` with large arguments the matrix representation of
    this Hamiltonian may not be strictly symmetric, but is approximately symmetric within
    machine precision.
    ```


See also [`HOCartesianContactInteractions`](@ref) and[`HOCartesianEnergyConservedPerDim`](@ref).
