```
function to_braket_ahs_ir(hamiltonian::BloqadeSchema.EffectiveHamiltonian)
```

Unwraps the `BloqadeSchema.RydbergHamiltonian` contained inside `hamiltonian` and immediately evaluates it using  `to_braket_ahs_ir(rydberg_hamiltonian::BloqadeSchema.RydbergHamiltonian)`
