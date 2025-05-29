```
totransfermap(nq::Integer, circuit::Vector{Gate}, thetas=nothing)
```

Computes the Pauli transfer map acting on `nq` qubits from a circuit with parameters `thetas`. `thetas` defaults to `nothing` but is required if the circuit contains parametrized gates. The returned lookup map is a vector of vectors like [(pstr1, coeff1), (pstr2, coeff2), ...], where the `pstr` are *partial* Pauli strings on the affected qubits.
