```
GateData
```

An object that stores all of the gate indices and data.

# Fields

  * `gate_indices::Vector{GateIndex}`: Indices for all gates.
  * `G::Int32`: Number of gates.
  * `N::Int32`: Number of indices.
  * `N_pad::Int32`: Number of padded indices.
  * `N_marginal::Int32`: Number of marginal indices.
  * `N_pad_marginal::Int32`: Number of padded marginal indices.
  * `N_relative::Int32`: Number of relative indices.
  * `N_pad_relative::Int32`: Number of padded relative indices.
  * `combined::Bool`: Whether to treat Pauli X, Y, and Z basis SPAM noise as the same.
  * `strict::Bool`: Whether to be strict about whether gates are deemed to be estimable to additive or relative precision.
