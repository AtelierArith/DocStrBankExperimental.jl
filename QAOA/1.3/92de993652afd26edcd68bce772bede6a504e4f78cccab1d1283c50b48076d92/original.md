```
cost_function(problem::Problem, beta_and_gamma::Vector{Float64})
```

Returns the QAOA cost function, i.e. the expectation value of the problem Hamiltonian.

### Input

  * `problem::Problem`: A `Problem` instance defining the optimization problem.
  * `beta_and_gamma::Vector{Float64}`: A vector of QAOA parameters.

### Output

  * The expectation value of the problem Hamiltonian.

### Notes

This function computes

$\langle \hat H \rangle = \left\langle \sum_{i=1}^N\left( h_i \hat Z_i + \sum_{j>i} J_{ij}\hat Z_i \hat Z_j \right)\right\rangle,$

where $N$ is `num_qubits`, $h_i$ are the `local_fields` and $J_{ij}$ are the `couplings` from `problem`.
