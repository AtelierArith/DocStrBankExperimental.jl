```
Problem(num_layers::Int, local_fields::Vector{Real}, couplings::Matrix{Real}, driver)
```

A container holding the basic properties of the QAOA circuit.

  * `num_qubits::Int64`: The number of qubits of the QAOA circuit.
  * `num_layers::Int64`: The number of layers $p$ of the QAOA circuit.
  * `local_fields::Vector{Real}`: The local (magnetic) fields of the Ising problem Hamiltonian.
  * `couplings::Matrix{Real}`: The coupling matrix of the Ising problem Hamiltonian.
  * `edges::Any`: The edges of the graph specified by the coupling matrix.
  * `driver::Any`: The driver of the QAOA circuit. By default the Pauli matrix `X`. May also be set to,     e.g., `[[X, X], [Y, Y]]` to obtain the drivers$\hat X_i \hat X_j + \hat Y_i \hat Y_j$ acting on every pair of connected qubits.
