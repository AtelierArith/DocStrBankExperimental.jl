```
thermal_state(T, mu_array, Ham, aggIndices; 
	boltzmann_const = 0.69503476, diagonalize = false, diagonal = false)
```

Get initial state as thermal state excited with ultra-fast laser pulse. In this version we suppose that after the thermal state is excited with laser pulse, the whole population  of ground state is distributed over electric states in `mu_array`. We assume  Condon approximation.

$\rho_\text{thermal} = \exp( -\frac{i}{\hbar} H ), \quad \hbar = 1$`.

# Arguments

  * `T`: Temperature of the initial thermal state.
  * `mu_array`: Vector of electric states in local basis, see [`electronicIndices`](@ref). The first       index is for ground state of the aggregate the rest are first excited states in local basis.
  * `Ham`: Arbitrary operator specifying the Hamiltonian.
  * `aggIndices`: Aggregate indices, see [`getIndices`](@ref).
  * `boltzmann_const`: Boltzmann const in $\mathrm{cm^{-1}}$.
  * `diagonalize`: Decompose Hamiltonian into $\lambda_i, S, S^{-1}$       and calculate the exponential using eigenvalue decomposition.
  * `diagonal`: Return only the diagonal part of the excited density matrix.
