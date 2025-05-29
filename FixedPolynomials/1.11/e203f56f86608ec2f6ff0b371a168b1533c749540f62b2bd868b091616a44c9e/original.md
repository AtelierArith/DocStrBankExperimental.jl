```
evaluate_and_jacobian!(u, U, F, x, cfg::JacobianConfig)
```

Evaluate `F` and its Jacobian at `x` using the precomputated values in `cfg` and store the result in `u` and `U` (Jacobian).

### Example

```julia
evaluate_and_jacobian!(u, U, F, x, config(F, x))
```
