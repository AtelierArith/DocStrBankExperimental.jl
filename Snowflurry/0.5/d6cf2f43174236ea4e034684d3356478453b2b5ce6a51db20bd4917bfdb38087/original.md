```
SwapQubitsForAdjacencyTranspiler
```

Transpiler stage which adds `Swap` gates around multi-qubit gates so that the  final `Operator` acts on adjacent qubits. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Fields

  * `connectivity::AbstractConnectivity` – Connectivity for the placement of `Swap` gates.

# Examples

```jldoctest
julia> transpiler = SwapQubitsForAdjacencyTranspiler(LineConnectivity(6));

julia> circuit = QuantumCircuit(qubit_count = 6, instructions = [toffoli(4, 6, 1)])
Quantum Circuit Object:
   qubit_count: 6 
   bit_count: 6 
q[1]:──X──
       |  
q[2]:──|──
       |  
q[3]:──|──
       |  
q[4]:──*──
       |  
q[5]:──|──
       |  
q[6]:──*──
          




julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 6 
   bit_count: 6 
q[1]:───────────────────────────X───────────────────────────
                                |                           
q[2]:───────☒───────────────────*───────────────────☒───────
            |                   |                   |       
q[3]:──☒────☒──────────────☒────*────☒──────────────☒────☒──
       |                   |         |                   |  
q[4]:──☒──────────────☒────☒─────────☒────☒──────────────☒──
                      |                   |                 
q[5]:────────────☒────☒───────────────────☒────☒────────────
                 |                             |            
q[6]:────────────☒─────────────────────────────☒────────────
                                                            



julia> compare_circuits(circuit, transpiled_circuit)
true

```
