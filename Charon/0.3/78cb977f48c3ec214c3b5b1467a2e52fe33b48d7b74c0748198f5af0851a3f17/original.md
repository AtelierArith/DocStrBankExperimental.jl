```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, dicefile::AbstractString, messages::Integer=nsteps÷100, scalingmessages::Bool=true)
```

dicefile is a (zipped) CSV-file in DICE 2-pop format: It should contain exactly four columns, the first one contains the number of ancestral reads, the second the number of derived reads, the third the frequency of the derived allele in the anchor population and the fourth the number of loci with exactly this combination of data.
