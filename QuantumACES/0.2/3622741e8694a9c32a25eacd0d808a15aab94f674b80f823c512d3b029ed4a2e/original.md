```
get_wht_matrix(n::Integer; inverse::Bool = false)
get_wht_matrix(gate::Gate; inverse::Bool = false)
```

Returns the symplectically ordered Walsh-Hadamard transform matrix of order `n`, the number of qubits on which the gate `gate` acts, which maps an n-qubit Pauli error probability distribution to its eigenvalues, or the inverse transform if `inverse` is `true`.
