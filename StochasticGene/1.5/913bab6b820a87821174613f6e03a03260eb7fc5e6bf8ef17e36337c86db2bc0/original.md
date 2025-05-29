```
GMmodel{RateType, PriorType, ProposalType, ParamType, MethodType, ComponentType, ReporterType}
```

Structure for GM models.

# Fields

  * `rates::RateType`: Transition rates.
  * `Gtransitions::Tuple`: Tuple of vectors of G state transitions.
  * `G::Int`: Number of G steps.
  * `nalleles::Int`: Number of alleles producing RNA.
  * `rateprior::PriorType`: Prior distribution for rates.
  * `proposal::ProposalType`: MCMC proposal distribution.
  * `fittedparam::ParamType`: Indices of rates to be fitted.
