```
evolve!(S::Vector{<:Vector{<:Real}}, h::Vector{<:Real}, J::Matrix{<:Real}, β::Vector{<:Real}, γ::Vector{<:Real})
```

### Input

  * `S::Vector{<:Vector{<:Real}}`: The initial vector of all spin vectors.
  * `h::Vector{<:Real}`: The vector of local magnetic fields of the problem Hamiltonian.
  * `J::Matrix{<:Real}`: The coupling matrix  of the problem Hamiltonian.
  * `β::Vector{<:Real}`: The vector of QAOA driver parameters.
  * `γ::Vector{<:Real}`: The vector of QAOA problem parameters.

### Output

  * The input `S` is now the vector of all spin vectors after a full mean-field AOA evolution.

### Notes

  * This is the first dispatch of `evolve`, which only returns the final vector of spin vectors.
  * The vector of spin vectors is properly initialized as

    `S = [[1., 0., 0.] for _ in 1:num_qubits]`.
