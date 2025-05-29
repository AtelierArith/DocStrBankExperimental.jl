```
overlapwithpaulisum(psum1::PauliSum, psum2::PauliSum)
```

Calculates the overlap between two `PauliSum`s. Important: We assume 'normalized' Pauli strings, i.e. such that `Tr[P^2] = 1` for any `n`-qubit Pauli string P. If one Pauli sum represents e.g. a normalized quantum state, the result will need to be scaled by `2^n`.  
