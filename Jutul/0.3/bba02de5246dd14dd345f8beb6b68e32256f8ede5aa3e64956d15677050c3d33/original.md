```
HelperSimulator(model::M, T = Float64; state0 = setup_state(model), executor::E = Jutul.default_executor()) where {M, E}
```

Construct a helper simulator that can be used to compute the residuals and/or accumulation terms for a given type T. Useful for coupling Jutul to other solvers and types of automatic differentiation.
