```
RiskEvent(Prob, Distribution, Trials; seed=0)
```

Risk Events are defined as conditional distributions that will inflate the 0.

The RiskEvent() allows you to conditionally sample any distribution for as many trials as defined. *Prob* is the conditional probability of sampling the impact Distribution *Distribution* is any univariate distribution from Distributions.jl *Trials* is the number of total iterations. *seed* allows you to set a seed for the RiskEvent. Left blank or set to 0, the seed is set to random.
