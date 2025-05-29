```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, coverages::AbstractVector{<:Integer}, derivedreads::AbstractVector{<:Integer}, frequencies::AbstractVector{<:Real}, counts::AbstractVector{<:Integer}, messages::Integer=nsteps÷100, scalingmessages::Bool=true)
```

MCMC with simulated proposals. There are counts[i] loci with coverage coverages[i], derivedreads[i] derived alleles and frequency frequencies[i] in the anchor population. 
