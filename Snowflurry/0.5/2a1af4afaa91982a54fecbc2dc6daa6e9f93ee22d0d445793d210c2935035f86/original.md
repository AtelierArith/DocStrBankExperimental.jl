```
SimplifyRxGatesTranspiler
```

Transpiler stage which finds `RotationX` gates in an input circuit and, based on their  angle theta, casts them to one of the right-angle `RotationX` gates  (`SigmaX`, `X90`, or `XM90`). In the case where `theta≈0.`, the gate is removed. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

# Fields

  * `atol::Real` – Absolute tolerance for the comparison of rotation angles (default = 1e-6).

# Examples

```jldoctest
julia> transpiler = SimplifyRxGatesTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [rotation_x(1, pi/2)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Rx(1.5708)──
                   
q[2]:──────────────
                   

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X_90──
             
q[2]:────────
             

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [rotation_x(1, pi)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Rx(3.1416)──
                   
q[2]:──────────────
                   


julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X──
          
q[2]:─────
          

julia> compare_circuits(circuit, transpiled_circuit)
true

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [rotation_x(1, 0.)])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──Rx(0.0000)──
                   
q[2]:──────────────
                   


julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:
     



julia> compare_circuits(circuit, transpiled_circuit)
true

```
