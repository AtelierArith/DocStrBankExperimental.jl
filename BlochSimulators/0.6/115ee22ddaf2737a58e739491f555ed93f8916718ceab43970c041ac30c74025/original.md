```
simulate_derivatives_finite_difference(sequence, parameters)
```

If only a `sequence` and `parameters` are provided, calculate the `echos` and then calculate the partial derivatives of `echos` w.r.t. the non-linear tissue properties using finite differences with the default stepsizes. Returns both the `echos` and the partial derivatives `∂echos`.
