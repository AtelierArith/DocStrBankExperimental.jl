```
get_marginal_wht_matrix(gate::Gate; inverse::Bool = false)
```

Returns the symplectically ordered Walsh-Hadamard transform matrix for the gate `gate`, marginalised over gate orbits, which maps the marginal Pauli error probability distribution to its marginal eigenvalues, or the inverse transform if `inverse` is `true`.
