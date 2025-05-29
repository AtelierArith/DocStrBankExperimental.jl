```
qcnncircuit(nqubits::Integer; periodic=false)
```

Create a Quantum Convolutional Neural Network (QCNN) circuit on `nqubits` qubits. The topology for the circuit is created by creating bricklayer topologies on half the qubits every layer. The final qubits are qubit 1 and ~`nqubits/2`, which should be measured.
