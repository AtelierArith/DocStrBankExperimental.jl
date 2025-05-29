```
BayesModel(prior, logintegrand) <: AbstractBQModel
```

Model inheriting from `AbstractMCMC.AbstractModel`. `prior` should be a multivariate distribution from `Distributions.jl` at the moment `prior` has to be a `MvNormal` but this will improved in a later version `logintegrand` should be the log of the function to integrate.
