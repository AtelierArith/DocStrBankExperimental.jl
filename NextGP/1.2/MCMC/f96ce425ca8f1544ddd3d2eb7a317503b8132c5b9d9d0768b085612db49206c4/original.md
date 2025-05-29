```
function runLMEM(formula,userData,nChain,nBurn,nThin;myHints=Dict{Symbol,Any}(),blockThese=[],outFolder="outMCMC",VCV=[],userPedData=[],summaryStat=Dict{Any,Any}())
```

  * `formula` is the model equatio as made available by the [`StatsModels.jl`](https://juliastats.org/StatsModels.jl/latest/) package
  * `userData` is a `DataFrame` including `lhs` and `rhs` variables (other than defined by `PED` and `SNP`)
  * `nChain`,`nBurn` and `nThin` are the chain length, burn-in period, and the thining interval used for the MCMC sampling
  * Users can define coding of their variables (e.g. full dummy coding) by providing `myHints`. Check `StatsModels.jl`'s manual for [`categorical data`](https://juliastats.org/StatsModels.jl/latest/contrasts/#Modeling-categorical-data) could be useful.
