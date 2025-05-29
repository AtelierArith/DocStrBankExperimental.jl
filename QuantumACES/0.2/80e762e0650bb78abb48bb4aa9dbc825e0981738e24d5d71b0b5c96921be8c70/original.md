```
Pauli
```

Boolean representation of a Pauli operator.

# Fields

  * `pauli::Vector{Bool}`: The Pauli operator stored as a Boolean vector. The first `qubit_num` elements represent Pauli X on each qubit, the next `qubit_num` elements represent Pauli Z on each qubit, and the final element represents the sign.
  * `qubit_num::Int16`: The number of qubits on which the Pauli operator acts; the length of the vector is `2 * qubit_num + 1`.
