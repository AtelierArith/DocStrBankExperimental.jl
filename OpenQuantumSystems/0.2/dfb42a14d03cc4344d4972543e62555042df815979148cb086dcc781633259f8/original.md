```
thermal_state_composite(T, mu_weighted, Ham, aggIndices; 
	boltzmann_const::Float64 = 0.69503476, diagonalize::Bool=false, diagonal=false)
```

Functionality of this method is similar to [`thermal_state`](@ref), but the final  state is constructed from partial `thermal_states` with weight specified in `mu_weighted`. For example 

`julia thermal_state_composite(T, [0.0, 0.8, 0.2], ...) = 0.8 * thermal_state(T, [1, 2, 1], ...) + 0.2 * thermal_state(T, [1, 1, 2], ...)``

$\rho_\text{thermal} = \exp( -\frac{i}{\hbar} H ), \quad \hbar = 1$.

# Arguments

  * `T`: Temperature of the initial thermal state.
  * `mu_weighted`: Vector of weights of electric states in local basis, see [`electronicIndices`](@ref).
  * `Ham`: Arbitrary operator specifying the Hamiltonian.
  * `aggIndices`: Aggregate indices, see [`getIndices`](@ref).
  * `boltzmann_const`: Boltzmann const in $\mathrm{cm^{-1}}$.
  * `diagonalize`: Decompose Hamiltonian into $\lambda_i, S, S^{-1}$       and calculate the exponential using eigenvalue decomposition.
  * `diagonal`: Return only the diagonal part of the excited density matrix.
