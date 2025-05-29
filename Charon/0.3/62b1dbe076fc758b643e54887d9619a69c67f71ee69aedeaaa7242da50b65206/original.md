```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, sedimentdata::DataFrame, frequencies::DataFrame; messages::Integer=nsteps÷100, scalingmessages::Bool=true)
```

sedimentdata is a path to a DataFrame, where the first column are the derived reads, and the second column are the coverages. frequencies is a DataFrame with one column, containing frequencies of the anchor population. The number of rows of both files should be the same.
