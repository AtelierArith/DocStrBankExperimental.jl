```
function collective_coupling(op, num_qubit; sp = false, unit = :h)
```

Create `ConstantCouplings` object with operator `op` on each qubits. `op` is the string representation of one of the Pauli matrices. `num_qubit` is the total number of qubits. `sp` set whether to use sparse matrices. `unit` set the unit one – `:h` or `:ħ`.
