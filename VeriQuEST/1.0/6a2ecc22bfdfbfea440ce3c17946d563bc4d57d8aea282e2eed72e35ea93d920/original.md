```
initialise_qubit(dummy::DummyQubit, noinput::NoInputQubits, quantum_state, qubit_index, qubit_input_value::Int)
```

This function initialises a qubit in a quantum state. If the input value for the qubit is zero, it does nothing.  If the input value is one, it applies a Pauli-X gate to the qubit. If the input value is neither zero nor one,  it throws a `DummyQubitZeroOneInitialisationError`.

# Arguments

  * `dummy::DummyQubit`: The DummyQubit object.
  * `noinput::NoInputQubits`: The NoInputQubits object.
  * `quantum_state`: The quantum state containing the qubit.
  * `qubit_index`: The index of the qubit in the quantum state.
  * `qubit_input_value::Int`: The input value for the qubit.

# Examples

```julia
dummy = DummyQubit()
noinput = NoInputQubits()
quantum_state = createQureg(1, env)
qubit_index = 1
qubit_input_value = 0
initialise_qubit(dummy, noinput, quantum_state, qubit_index, qubit_input_value)
```
