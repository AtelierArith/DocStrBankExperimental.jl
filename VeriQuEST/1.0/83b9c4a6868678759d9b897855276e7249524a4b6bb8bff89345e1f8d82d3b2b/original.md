```
initialise_qubit(qubit::Union{ComputationQubit,TrapQubit}, input::Union{InputQubits,InputQubits,NoInputQubits}, quantum_state, qubit_index, qubit_input_value::Float64)
```

This function initialises a qubit in a quantum state with a phase determined by the input value.  If the input value is a float, it initialises the qubit to a superposition state with the input value as the phase.  If the input value is not a float, it throws a `QubitFloatPhaseInitialisationError`.

# Arguments

  * `qubit::Union{ComputationQubit,TrapQubit}`: The type of the qubit.
  * `input::Union{InputQubits,InputQubits,NoInputQubits}`: The input object.
  * `quantum_state`: The quantum state containing the qubit.
  * `qubit_index`: The index of the qubit in the quantum state.
  * `qubit_input_value::Float64`: The input value for the qubit, which determines the phase.

# Examples

```julia
qubit = ComputationQubit()
input = InputQubits()
quantum_state = createQureg(1, env)
qubit_index = 1
qubit_input_value = 0.5
initialise_qubit(qubit, input, quantum_state, qubit_index, qubit_input_value)
```
