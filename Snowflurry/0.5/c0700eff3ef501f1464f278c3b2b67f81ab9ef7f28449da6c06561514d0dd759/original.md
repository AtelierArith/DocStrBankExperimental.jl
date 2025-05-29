```
DecomposeSingleTargetSingleControlGatesTranspiler
```

Transpiler stage which finds single-control, single-target `Controlled` gates in an input circuit and casts them into a sequence of `RotationZ` (Rz), `ControlX`, `Universal` (U) and `PhaseShift` (P) gates in a new, equivalent circuit. For reference, see Nielsen and Chuang, "Quantum Computation and Quantum Information", p. 180. The input and output circuits perform the same operation on an arbitrary state `Ket` (up to a global phase).

!!! note
    If a global phase is applied by the kernel of the `Controlled` gate on the target  qubit, this decomposition preserves it.


For instance, `rotation_z(pi)` and `phase_shift(pi)` kernels will yield results with a phase offset.

# Examples

```jldoctest
julia> transpiler = DecomposeSingleTargetSingleControlGatesTranspiler();

julia> circuit = QuantumCircuit(
                    qubit_count = 2,
                    instructions = [sigma_x(1), controlled(rotation_z(2, pi), [1])]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X────────*───────
                |       
q[2]:───────Rz(3.1416)──
                        
julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X───────────────────*──────────────────────────────────────*───────────────────────────────────
                           |                                      |                                   
q[2]:───────Rz(-1.5708)────X────U(θ=0.0000,ϕ=-1.5708,λ=0.0000)────X────U(θ=0.0000,ϕ=3.1416,λ=0.0000)──
                                                                                                      
julia> compare_circuits(circuit, transpiled_circuit)
true

julia> simulate(transpiled_circuit)
4-element Ket{ComplexF64}:
0.0 + 0.0im
-0.0 + 0.0im
0.7071067811865477 - 0.7071067811865474im
0.0 + 0.0im

julia> circuit = QuantumCircuit(
                    qubit_count = 2,
                    instructions = [sigma_x(1), controlled(phase_shift(2, pi), [1])]
                )
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X────────*──────
                |      
q[2]:───────P(3.1416)──
                       

julia> transpiled_circuit = transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X───────────────────*──────────────────────────────────────*─────────────────────────────────────P(1.5708)──
                           |                                      |                                                
q[2]:───────Rz(-1.5708)────X────U(θ=0.0000,ϕ=-1.5708,λ=0.0000)────X────U(θ=0.0000,ϕ=3.1416,λ=0.0000)───────────────
                                                                                                                   

julia> compare_circuits(circuit,transpiled_circuit)
true

julia> simulate(circuit)
4-element Ket{ComplexF64}:
0.0 + 0.0im
0.0 + 0.0im
1.0 + 0.0im
0.0 + 0.0im

```
