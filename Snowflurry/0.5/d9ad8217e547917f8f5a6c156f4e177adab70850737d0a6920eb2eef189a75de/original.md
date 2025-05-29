```
CastCXToCZGateTranspiler
```

Transpiler stage which expands all `CX` gates into `CZ` and `Hadamard` gates. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler = CastCXToCZGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [control_x(1, 2)])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──*──
       |
q[2]:──X──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:───────*───────
            |
q[2]:──H────Z────H──
```
