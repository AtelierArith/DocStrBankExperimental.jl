```
totransfermap(ptm::Matrix)
```

Computes the Pauli transfer map acting on `nq` qubits from a Pauli Transfer Matrix (PTM). The PTM should be the matrix representation of a gate in Pauli basis. The returned lookup map is a vector of vectors like [(pstr1, coeff1), (pstr2, coeff2), ...], where the `pstr` are *partial* Pauli strings on the affected qubits.
