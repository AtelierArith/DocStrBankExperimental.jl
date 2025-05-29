```
init_plus_phase_state!(nophase::NoPhase, qureg, qᵢ)
```

This function initializes a quantum state to a superposition state (|+⟩ state) without adding any phase.  It applies a Hadamard gate to the qubit, putting it into a superposition state.

# Arguments

  * `nophase::NoPhase`: The NoPhase object indicating that no phase is to be added.
  * `qureg`: The quantum register containing the qubit.
  * `qᵢ`: The index of the qubit in the quantum register.

# Examples

```julia
nophase = NoPhase()
qureg = createQureg(1, env)
qᵢ = 1
init_plus_phase_state!(nophase, qureg, qᵢ)
```
