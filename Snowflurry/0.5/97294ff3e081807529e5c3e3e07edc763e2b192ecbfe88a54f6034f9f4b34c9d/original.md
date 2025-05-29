```
CastToffoliToCXGateTranspiler
```

Transpiler stage which expands all Toffoli gates into `CX` gates and single-qubit gates. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler = CastToffoliToCXGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 3, instructions = [toffoli(1, 2, 3)])
Quantum Circuit Object:
   qubit_count: 3
   bit_count: 3
q[1]:──*──
       |
q[2]:──*──
       |
q[3]:──X──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──────────────────*────────────────────*──────────────*─────────T──────────*──
                       |                    |              |                    |  
q[2]:───────*──────────|─────────*──────────|────T─────────X──────────────T†────X──
            |          |         |          |                                      
q[3]:──H────X────T†────X────T────X────T†────X─────────T─────────H──────────────────
                                                                                   

```
