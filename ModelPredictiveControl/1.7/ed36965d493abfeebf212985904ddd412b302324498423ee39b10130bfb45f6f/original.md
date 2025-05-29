```
ExplicitMPC(estim::StateEstimator; <keyword arguments>)
```

Use custom state estimator `estim` to construct `ExplicitMPC`.

`estim.model` must be a [`LinModel`](@ref). Else, a [`NonLinMPC`](@ref) is required.
