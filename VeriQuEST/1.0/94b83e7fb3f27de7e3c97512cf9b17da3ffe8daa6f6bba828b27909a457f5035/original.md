```
init_plus_phase_state!(phase::Phase, qureg, qᵢ, φᵢ)
```

This function initializes a quantum state to a superposition state (|+⟩ state) with a specified phase.  It first applies a Hadamard gate to the qubit, putting it into a superposition state.  Then it applies a Z rotation to the qubit, adding the specified phase.

# Arguments

  * `phase::Phase`: The phase object.
  * `qureg`: The quantum register containing the qubit.
  * `qᵢ`: The index of the qubit in the quantum register.
  * `φᵢ`: The phase to be added to the qubit.

# Examples

```julia
phase = Phase()
qureg = createQureg(1, env)
qᵢ = 1
φᵢ = π/2
init_plus_phase_state!(phase, qureg, qᵢ, φᵢ)
```
