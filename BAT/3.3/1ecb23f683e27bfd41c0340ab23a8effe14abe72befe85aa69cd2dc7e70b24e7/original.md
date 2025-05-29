```
struct MetropolisHastings <: MCMCAlgorithm
```

Metropolis-Hastings MCMC sampling algorithm.

Constructors:

  * `MetropolisHastings(; fields...)`

Fields:

  * `proposal::Distributions.ContinuousDistribution`: Default: TDist(1.0)
  * `weighting::BAT.AbstractMCMCWeightingScheme`: Default: RepetitionWeighting()
  * `tuning::BAT.MHProposalDistTuning`: Default: AdaptiveMHTuning()
