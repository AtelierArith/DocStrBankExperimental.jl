```
CastSwapToCZGateTranspiler
```

Transpiler stage which expands all Swap gates into `CZ` gates and single-qubit gates. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler = CastSwapToCZGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [swap(1, 2)])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──☒──
       |
q[2]:──☒──

julia> transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:───────────*────Y_m90────────────*────Y_90─────────────*──────────
                |                     |                     |          
q[2]:──Y_m90────Z─────────────Y_90────Z────────────Y_m90────Z────Y_90──
                                              

```
