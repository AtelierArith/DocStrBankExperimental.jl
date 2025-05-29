```
CastUniversalToRzRxRzTranspiler
```

Transpiler stage which finds `Universal` gates in an input circuit and casts them into a sequence of `PhaseShift` (P), `RotationX` (Rx) and `PhaseShift` (P) gates in a new circuit. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler = CastUniversalToRzRxRzTranspiler();

julia> circuit = QuantumCircuit(
                    qubit_count = 2,
                    instructions = [universal(1, π/2, π/4, π/8)]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──U(θ=1.5708,ϕ=0.7854,λ=0.3927)──
                                      
q[2]:─────────────────────────────────
                                      

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(-1.1781)────Rx(1.5708)────P(2.3562)──
                                              
q[2]:─────────────────────────────────────────
                                              

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [universal(1, 0, π/4, 0)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──U(θ=0.0000,ϕ=0.7854,λ=0.0000)──
                                      
q[2]:─────────────────────────────────
                                      

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(-1.5708)────Rx(0.0000)────P(2.3562)──
                                              
q[2]:─────────────────────────────────────────
                                              

julia> compare_circuits(circuit,transpiled_circuit)
true

```
