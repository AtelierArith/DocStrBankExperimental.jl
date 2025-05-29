```
toffoli_circuit(trg, cntrl, N)
```

construct the circuit for decomposing the Toffoli gate in Figure 4.9 of Nielsen and Chuang (2000). the constructed toffoli gate acts in circuit of `N` qubits, has controls     on wires in Tuple `cntrl` and has target on wire `trg`. returns a `CircuitGateChain{N}` object.
