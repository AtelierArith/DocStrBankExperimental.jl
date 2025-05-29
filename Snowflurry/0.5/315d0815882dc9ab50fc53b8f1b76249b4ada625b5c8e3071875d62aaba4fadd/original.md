```
RejectNonNativeInstructionsTranspiler
```

Transpiler stage which throws a `DomainError` if a non-native `Instruction` is found in the `circuit`. The `circuit` remains unchanged if no error is thrown.

See [`is_native_instruction`](@ref) for additional information about native instructions.

# Fields

  * connectivity::AbstractConnectivity – Connectivity which specifies the connections on                                       which two-qubit gates can be applied.
  * native_gates::Vector{DataType} – List of native gates. The gates that are native to the                                   Anyon QPUs are used by default.

# Examples

```jldoctest
julia> connectivity = LineConnectivity(4)
LineConnectivity{4}
1──2──3──4


julia> default_transpiler = RejectNonNativeInstructionsTranspiler(connectivity);


julia> invalid_circuit = QuantumCircuit(
           qubit_count = 4,
           instructions = [sigma_x(4), control_z(1, 3)],
           )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:───────*──
            |  
q[2]:───────|──
            |  
q[3]:───────Z──
               
q[4]:──X───────
               

julia> transpile(default_transpiler, invalid_circuit)
ERROR: DomainError with LineConnectivity{4}
1──2──3──4
[...]


julia> valid_circuit = QuantumCircuit(
           qubit_count = 4,
           instructions = [sigma_x(4), control_z(1, 2)],
           )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:───────*──
            |  
q[2]:───────Z──
               
q[3]:──────────
               
q[4]:──X───────
               

julia> transpiled_circuit = transpile(default_transpiler, valid_circuit)
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:───────*──
            |  
q[2]:───────Z──
               
q[3]:──────────
               
q[4]:──X───────


julia> custom_circuit = QuantumCircuit(
                  qubit_count = 4,
                  instructions = [control_x(2, 3)],
                  )
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:─────
          
q[2]:──*──
       |  
q[3]:──X──
          
q[4]:─────
          

julia> transpile(default_transpiler, custom_circuit)
ERROR: DomainError with LineConnectivity{4}
1──2──3──4
[...]


julia> custom_transpiler = RejectNonNativeInstructionsTranspiler(
            connectivity,
            [Snowflurry.ControlX]
        );


julia> transpiled_circuit = transpile(custom_transpiler, custom_circuit)
Quantum Circuit Object:
   qubit_count: 4 
   bit_count: 4 
q[1]:─────
          
q[2]:──*──
       |  
q[3]:──X──
          
q[4]:─────
          

```
