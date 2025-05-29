```
initialise_qubit(mbqc::MBQC, qubit::Union{ComputationQubit,TrapQubit}, input::Union{InputQubits,InputQubits,NoInputQubits}, quantum_state, qubit_index)
```

This function initialises a qubit in a quantum state to a superposition state without adding any phase.  It applies a Hadamard gate to the qubit, putting it into a superposition state.

# Arguments

  * `mbqc::MBQC`: The MBQC object.
  * `qubit::Union{ComputationQubit,TrapQubit}`: The type of the qubit.
  * `input::Union{InputQubits,InputQubits,NoInputQubits}`: The input object.
  * `quantum_state`: The quantum state containing the qubit.
  * `qubit_index`: The index of the qubit in the quantum state.

# Examples

```julia
mbqc = MBQC()
qubit = ComputationQubit()
input = InputQubits()
quantum_state = createQureg(1, env)
qubit_index = 1
initialise_qubit(mbqc, qubit, input, quantum_state, qubit_index)
```
