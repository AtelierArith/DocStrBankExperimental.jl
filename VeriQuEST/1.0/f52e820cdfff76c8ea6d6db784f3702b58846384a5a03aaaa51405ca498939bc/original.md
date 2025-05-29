```
create_quantum_state(client::Client, state::StateVector, quantum_env, num_qubits)
```

Create a new quantum state as a state vector using the QuEST function `createQureg`.

# Arguments

  * `client::Client`: The client for which the quantum state is being created.
  * `state::StateVector`: Indicates that the quantum state should be created as a state vector.
  * `quantum_env`: The quantum environment in which the quantum state is being created.
  * `num_qubits`: The number of qubits in the quantum state.

# Returns

  * A new quantum state as a state vector.

# Examples

```julia
client = Client()
env = create_quantum_env(client)
state = create_quantum_state(client, StateVector(), env, 2)
```
