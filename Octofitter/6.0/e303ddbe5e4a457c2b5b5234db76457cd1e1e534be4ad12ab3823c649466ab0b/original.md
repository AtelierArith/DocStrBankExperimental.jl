```
prior_only_model(system, θ=drawfrompriors(system))
```

Creates a copy of a system model that is stripped of observations. The result is  a model that only samples from the priors. This can be used eg. for tempering.
