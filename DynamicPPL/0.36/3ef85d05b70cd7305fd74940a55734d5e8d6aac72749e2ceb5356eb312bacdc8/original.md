```
predict([rng::AbstractRNG,] model::Model, chain::AbstractVector{<:AbstractVarInfo})
```

Generate samples from the posterior predictive distribution by evaluating `model` at each set of parameter values provided in `chain`. The number of posterior predictive samples matches the length of `chain`. The returned `AbstractVarInfo`s will contain both the posterior parameter values and the predicted values.
