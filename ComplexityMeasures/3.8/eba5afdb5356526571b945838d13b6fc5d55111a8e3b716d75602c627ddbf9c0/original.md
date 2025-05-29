```
information_normalized([e::DiscreteInfoEstimator,] [est::ProbabilitiesEstimator,] o::OutcomeSpace, x) → h::Real
```

Estimate the normalized version of the given discrete information measure, This is just the value of [`information`](@ref) divided its maximum possible value given `o`.

The same convenience syntaxes as in [`information`](@ref) can be used here.

Notice that there is no method `information_normalized(e::DiscreteInfoEstimator, probs::Probabilities)`, because there is no way to know the number of *possible* outcomes (i.e., the [`total_outcomes`](@ref)) from `probs`.

## Normalized values

For the [`PlugIn`](@ref) estimator, it is guaranteed that `h̃ ∈ [0, 1]`. For any other estimator, we can't guarantee this, since the estimator might over-correct. You should know what you're doing if using anything but [`PlugIn`](@ref) to estimate normalized values.
