```
bayesianupdating(likelihood, models, pointestimate; prior)
```

Perform bayesian updating using the given `likelihood`, `models`  and any point estimation method [`AbstractBayesianPointEstimate`](@ref).

### Notes

Method can be called with an empty Vector of models, i.e.

```
bayesianupdating(likelihood, [], pointestimate)
```

If `prior` is not given, the method will construct a prior distribution from the prior specified in `AbstractBayesianPointEstimate.prior`.

`likelihood` is a Julia function which must be defined in terms of a `DataFrame` of samples, and must evaluate the likelihood for each row of the `DataFrame`

For example, a loglikelihood based on normal distribution using 'Data':

```julia
likelihood(df) = [sum(logpdf.(Normal.(df_i.x, 1), Data)) for df_i in eachrow(df)]
```

If a model evaluation is required to evaluate the likelihood, a vector of `UQModel`s must be passed to `bayesianupdating`. For example if the variable `x` above is the output of a numerical model.

For a general overview of the function, see [`bayesianupdating`](@ref).
