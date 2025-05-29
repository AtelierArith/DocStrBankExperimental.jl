```
req_wires(cg::CircuitGate{M,G})
```

Minimum number of required qubit wires in a circuit to host the circuit gate `cg`.

```jldoctest
julia> cg = circuit_gate(3, X, (1,2,5));
julia> req_wires(cg)
5
```
