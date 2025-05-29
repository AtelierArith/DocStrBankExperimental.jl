```
SimplifyRzGatesTranspiler
```

Transpiler stage which finds `PhaseShift` gates in an input circuit and, based on their  phase angle phi, casts them to one of the right-angle `RotationZ` gates (`SigmaZ`, `Z90`, `ZM90`, `Pi8` or `Pi8Dagger`). In the case where `phi≈0.`, the  gate is removed. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase). The tolerance  used for `Base.isapprox()` in each case can be set by passing an optional argument to the `Transpiler`, e.g: `transpiler=SimplifyRzGatesTranspiler(1.0e-10)`

# Fields

  * `atol::Real` – Absolute tolerance for the comparison of rotation angles (default = 1e-6).

# Examples

```jldoctest
julia> transpiler = SimplifyRzGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [phase_shift(1, pi/2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(1.5708)──
                  
q[2]:─────────────
                  

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z_90──
             
q[2]:────────
             

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [phase_shift(1, pi)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──P(3.1416)──
                  
q[2]:─────────────
                  

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Z──
          
q[2]:─────
          

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

```
