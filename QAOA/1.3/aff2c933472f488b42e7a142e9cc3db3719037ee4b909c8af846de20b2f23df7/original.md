```
expectation(S::Vector{<:Vector{<:Real}}, h::Vector{<:Real}, J::Matrix{<:Real})
```

### Input

  * `S::Vector{<:Vector{<:Real}}`: A vector of all spin vectors.
  * `h::Vector{<:Real}`: A vector of local magnetic fields.
  * `J::Matrix{<:Real}`: A coupling matrx.

### Output

  * The energy expectation value corresponding to the supplied spin configuration.

### Notes

  * In the mean-field approximation, the energy expectation value is defined as

    $\langle E \rangle = - \sum_{i=1}^N \bigg[ h_i + \sum_{j>i} J_{ij}  n_j^z(p) \bigg] n_i^z(p).$
