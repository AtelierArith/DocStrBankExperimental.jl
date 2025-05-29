```
CompressRzGatesTranspiler
```

Transpiler stage which gathers all Rz-type gates sharing a common target in an input  circuit and combines them into a single PhaseShift gate in a new circuit. Gates ordering may differ when gates are applied to different qubits,  but the input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Examples

```jldoctest
julia> transpiler = CompressRzGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_z(1), z_90(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z────Z_90──
                  
q[2]:─────────────
                  

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(-1.5708)──
                   
q[2]:──────────────
                   

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(
                    qubit_count = 3,
                    instructions = [sigma_z(1), pi_8(1), control_x(2,3), z_minus_90(1)]
                )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──Z────T─────────Z_m90──
                             
q[2]:────────────*───────────
                 |           
q[3]:────────────X───────────
                             

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──P(2.3562)───────
                       
q[2]:───────────────*──
                    |  
q[3]:───────────────X──
                       

julia> compare_circuits(circuit, transpiled_circuit)
true

```
