```
ll, e = correct!(pf, u, y, p = parameters(f), t = index(f))
```

Update state/weights based on measurement `y`,  returns log-likelihood and prediction error (the error is always 0 for particle filters).

# Extended help

To perform separate measurement updates for different sensors, see the ["Measurement models" in the documentation](@ref measurement_models). For [`AdvancedParticleFilter`](@ref), this can be realized by passing a custom `measurement_likelihood` function as the keyword argument `g` to `correct!`, or by calling the lower-level function `measurement_equation!` with a custom `measurement_likelihood`.
