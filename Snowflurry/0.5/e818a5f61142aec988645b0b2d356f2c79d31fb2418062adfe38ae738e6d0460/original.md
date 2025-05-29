```
CompressSingleQubitGatesTranspiler
```

Transpiler stage which gathers all single-qubit gates sharing a common target in an input  circuit and combines them into single `Universal` gates in a new circuit. Gate ordering may differ when gates are applied to different qubits,  but the input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler = CompressSingleQubitGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_x(1), sigma_y(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X────Y──
               
q[2]:──────────
               



julia> transpiled_circuit=transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──U(θ=0.0000,ϕ=3.1416,λ=0.0000)──
                                      
q[2]:─────────────────────────────────
                                      



julia> compare_circuits(circuit,transpiled_circuit)
true

julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [
                        sigma_x(1)
                        sigma_y(1)
                        control_x(2,3)
                        phase_shift(1,π/3)
                    ])
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────Y─────────P(1.0472)──
                                 
q[2]:────────────*───────────────
                 |               
q[3]:────────────X───────────────
                                 



julia> transpiled_circuit=transpile(transpiler,circuit)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──U(θ=0.0000,ϕ=-2.0944,λ=0.0000)───────
                                            
q[2]:────────────────────────────────────*──
                                         |  
q[3]:────────────────────────────────────X──
                                            




julia> compare_circuits(circuit,transpiled_circuit)
true

```
