Implementation of the No U-Turn Sampler for MCMC.

Please [read the documentation](https://tamaspapp.eu/DynamicHMC.jl/dev/). For the impatient: you probably want to

1. define a log density problem (eg for Bayesian inference) using the `LogDensityProblems`

package, then

2. use it with [`mcmc_with_warmup`](@ref).
