```
solve_adjoint_sensitivities(model, states, reports_or_timesteps, G; extra_timing = false, state0 = setup_state(model), forces = setup_forces(model), raw_output = false, kwarg...)
```

Compute sensitivities of `model` parameter with name `target` for objective function `G`.

The objective function is at the moment assumed to be a sum over all states on the form: `obj = Σₙ G(model, state, dt_n, n, forces_for_step_n)`

Solves the adjoint equations: For model equations F the gradient with respect to parameters p is     ∇ₚG = Σₙ (∂Fₙ / ∂p)ᵀ λₙ where n ∈ [1, N]. Given Lagrange multipliers λₙ from the adjoint equations     (∂Fₙ / ∂xₙ)ᵀ λₙ = - (∂J / ∂xₙ)ᵀ - (∂Fₙ₊₁ / ∂xₙ)ᵀ λₙ₊₁ where the last term is omitted for step n = N and G is the objective function.
