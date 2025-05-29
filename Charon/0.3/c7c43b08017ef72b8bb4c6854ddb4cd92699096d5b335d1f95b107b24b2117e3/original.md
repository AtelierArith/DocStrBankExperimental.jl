```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, coverages::AbstractVector{<:Integer}, derivedreads::AbstractVector{<:Integer}, frequencies::AbstractVector{<:Real}, messages::Integer=nsteps÷100, scalingmessages::Bool=true)
```

coverages[i] is the coverage, derivedreads[i] the number of derived reads and frequencies[i] the frequency of the derived allele in the anchor population at locus i. 
