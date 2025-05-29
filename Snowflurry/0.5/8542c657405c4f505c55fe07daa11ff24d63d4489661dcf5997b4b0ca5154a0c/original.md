```
CastToPhaseShiftAndHalfRotationXTranspiler,
```

Transpiler stage which converts all single-qubit gates in the input circuit into combinations of `PhaseShift` and `RotationX` with angle π/2 in the output circuit. For any gate in the input circuit, the number of gates in the output varies between zero and 5. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Fields

  * `atol::Real` – Absolute tolerance for the comparison of rotation angles (default = 1e-6).

# Examples

```jldoctest
julia> transpiler = CastToPhaseShiftAndHalfRotationXTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_x(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X──
          
q[2]:─────
          



julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z────X_90────Z────X_m90──
                                                 
q[2]:───────────────────────────
                                                 



julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [sigma_y(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Y──
          
q[2]:─────
          



julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──X_90────Z────X_m90──

q[2]:──────────────────────
                                           



julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [universal(1, 0., 0., 0.)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──U(θ=0.0000,ϕ=0.0000,λ=0.0000)──
                                      
q[2]:─────────────────────────────────
                                      



julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:
     



julia> compare_circuits(circuit, transpiled_circuit)
true

```
