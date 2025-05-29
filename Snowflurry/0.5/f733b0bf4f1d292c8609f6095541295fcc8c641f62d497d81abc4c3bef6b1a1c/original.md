```
is_native_circuit(
    circuit::QuantumCircuit,
    connectivity::GeometricConnectivity,
    native_gates::Vector{DataType} = set_of_native_gates,
)::Tuple{Bool,String}
```

Returns `(true, "")` if the `circuit` only contains native instructions for the `connectivity` and the list of possible `native_gates`. It returns `(false, "error_message")` otherwise. The native gates for the Anyon QPUs are used by default.

See [`is_native_instruction`](@ref) for more details about the identification of native instructions.

# Example

```jldoctest is_native_instruction
julia> connectivity = LineConnectivity(3)
LineConnectivity{3}
1──2──3


julia> native_circuit = QuantumCircuit(
           qubit_count = 3,
           instructions = [sigma_x(1), control_z(2, 3)]
       )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X───────
               
q[2]:───────*──
            |  
q[3]:───────Z──
               

julia> is_native_circuit(native_circuit, connectivity)
(true, "")

julia> foreign_circuit = QuantumCircuit(
                  qubit_count = 3,
                  instructions = [sigma_x(1), control_x(2, 3)]
              )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X───────
               
q[2]:───────*──
            |  
q[3]:───────X──
               

julia> is_native_circuit(foreign_circuit, connectivity)
(false, "Instruction type Gate{Snowflurry.ControlX} with targets [2, 3] is not native on the connectivity")

julia> is_native_circuit(
            foreign_circuit,
            connectivity,
            [Snowflurry.ControlX, Snowflurry.SigmaX]
        )
(true, "")

```

The folowing circuit is not native because the Toffoli gate is applied to more than two qubits:

```jldoctest is_native_instruction
julia> foreign_circuit = QuantumCircuit(
           qubit_count = 3,
           instructions = [sigma_x(1), toffoli(1, 2, 3)]
       )
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────*──
            |  
q[2]:───────*──
            |  
q[3]:───────X──
               

julia> is_native_circuit(
            foreign_circuit,
            connectivity,
            [Snowflurry.Toffoli, Snowflurry.SigmaX]
        )
(false, "Instruction type Gate{Snowflurry.Toffoli} with targets [1, 2, 3] is not native on the connectivity")

```
