```
apply(ρ::DensityMatrix, c::Circuit{N}) where {N}
```

Compute list of expectation values from measurement operators in `c.meas`, after applying circuit gates in `c.cgc` on the N-qubit density matrix `ρ`
