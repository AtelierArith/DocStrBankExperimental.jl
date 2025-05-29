```
CastISwapToCZGateTranspiler
```

Transpiler stage which expands all `ISwap` and `ISwapDagger` gates into `CZ` gates and single-qubit gates. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler = CastISwapToCZGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [iswap(1, 2)])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──x──
       |
q[2]:──x──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Y_m90─────────────*────Y_90─────────────*────Y_90──────────
                         |                     |                  
q[2]:───────────X_m90────Z────────────X_m90────Z────────────X_90──
                                                                  

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [iswap_dagger(1, 2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──x†──
       |   
q[2]:──x†──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Y_m90─────────────*────Y_m90────────────*────Y_90──────────
                         |                     |                  
q[2]:───────────X_m90────Z─────────────X_90────Z────────────X_90──

```
