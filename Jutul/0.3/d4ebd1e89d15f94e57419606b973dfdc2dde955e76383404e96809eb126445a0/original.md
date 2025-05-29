```
solve_adjoint_sensitivities!(∇G, storage, states, state0, timesteps, G; forces = setup_forces(model))
```

Non-allocating version of `solve_adjoint_sensitivities`.
