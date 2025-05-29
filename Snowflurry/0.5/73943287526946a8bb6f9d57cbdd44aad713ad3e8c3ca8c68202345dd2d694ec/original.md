```
compare_circuits(c0::QuantumCircuit, c1::QuantumCircuit)::Bool
```

Tests for the equivalence of two [`QuantumCircuit`](@ref) objects based on their effect on an arbitrary input state (a `Ket`). The circuits are equivalent if they both  yield the same output for any input, up to a global phase. Circuits with gates that are applied in a different order and to different targets can also be equivalent. 

!!! note
    If there are `Readout` instructions present on either `QuantumCircuit`,  `compare_circuits` checks that both circuits have readouts targeting the same qubits and that no operations exist on those qubits after readout.


# Examples

```jldoctest
julia> c0 = QuantumCircuit(qubit_count = 1, instructions = [sigma_x(1), sigma_y(1)])
Quantum Circuit Object:
   qubit_count: 1 
   bit_count: 1 
q[1]:──X────Y──
               



julia> c1 = QuantumCircuit(qubit_count = 1, instructions = [phase_shift(1, π)])
Quantum Circuit Object:
   qubit_count: 1  
   bit_count: 1  
q[1]:──P(3.1416)──
                  



julia> compare_circuits(c0, c1)
true            

julia> c0 = QuantumCircuit(
                qubit_count = 3,
                instructions = [sigma_x(1), sigma_y(1), control_x(2, 3)]
            )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────Y───────
                    
q[2]:────────────*──
                 |  
q[3]:────────────X──
                    



julia> c1 = QuantumCircuit(
                qubit_count = 3,
                instructions = [control_x(2, 3), sigma_x(1), sigma_y(1)]
            )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:───────X────Y──
                    
q[2]:──*────────────
       |            
q[3]:──X────────────
                    



julia> compare_circuits(c0, c1)
true    

julia> c2 = QuantumCircuit(qubit_count = 3, instructions = [sigma_x(1), readout(1, 1)])
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────✲──
               
q[2]:──────────
               
q[3]:──────────
               
julia> c3 = QuantumCircuit(qubit_count = 3, instructions = [sigma_x(1)])
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X──
          
q[2]:─────
          
q[3]:─────
          

julia> compare_circuits(c2,c3)
false    

```
