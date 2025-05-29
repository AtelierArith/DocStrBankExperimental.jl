```
SimplifyTrivialGatesTranspiler
```

Transpiler stage which removes gates that have no effect on the state `Ket` (e.g. `Identity`) and parameterized gates with null parameters (e.g. `rotation_x(target, 0.)`). The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase). The tolerance used for `Base.isapprox()` in each case can be set by passing an optional argument to the transpiler (e.g. `transpiler=SimplifyTrivialGatesTranspiler(1.0e-10)`).

# Fields

  * `atol::Real` – Absolute tolerance for the comparison of rotation angles (default = 1e-6).

# Examples

```jldoctest
julia> transpiler = SimplifyTrivialGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [identity_gate(1)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──I──
          
q[2]:─────
          
julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:      

julia> compare_circuits(circuit, transpiled_circuit)
true


julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [phase_shift(1, 0.)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(0.0000)──
                  
q[2]:─────────────
                  

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:      

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
