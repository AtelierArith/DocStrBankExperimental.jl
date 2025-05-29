```
QuantumCircuit(
    qubit_count::Int,
    bit_count::Int,
    instructions::Vector{AbstractInstruction},
    name::String = "default"
)
QuantumCircuit(circuit::QuantumCircuit)
```

A data structure which describes a *quantum circuit*.

# Fields

  * `qubit_count::Int` – Largest qubit index (e.g., specifying `qubit_count=n` enables the                       use of qubits 1 to n).
  * `bit_count::Int` – Optional: Number of classical bits (i.e., result register size).                     Defaults to `qubit_count` if unspecified.
  * `instructions::Vector{AbstractInstruction}` – Optional: Sequence of                                                `AbstractInstructions` (`Gates` and                                                `Readouts`) that operate on the qubits.                                                Defaults to an empty Vector.
  * `name::String` – Optional: Name of the circuit and the corresponding job. It is used to                   identify the job when it is sent to a hardware or virtual QPU.

# Examples

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:
     
q[2]:
```

A `QuantumCircuit` can be initialized with [`Gate`](@ref Gate) and [`Readout`](@ref Readout) structs:

```jldoctest circuit
julia> c = QuantumCircuit(
            qubit_count = 2,
            instructions = [
                hadamard(1),
                sigma_x(2),
                control_x(1, 2),
                readout(1, 1),
                readout(2, 2)
            ])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H─────────*────✲───────
                 |            
q[2]:───────X────X─────────✲──
                              
```

A deep copy of a `QuantumCircuit` can be obtained with the following function:

```jldoctest circuit
julia> c_copy = QuantumCircuit(c)
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H─────────*────✲───────
                 |            
q[2]:───────X────X─────────✲──
                              
```
