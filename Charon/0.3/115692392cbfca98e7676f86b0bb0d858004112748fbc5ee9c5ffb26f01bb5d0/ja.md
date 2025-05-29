```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, coverages::AbstractVector{<:Integer}, derivedreads::AbstractVector{<:Integer}, frequencies::AbstractVector{<:Real}, counts::AbstractVector{<:Integer}, messages::Integer=nsteps÷100, scalingmessages::Bool=true)
```

シミュレーションされた提案によるMCMC。counts[i]のロキがあり、カバレッジcoverages[i]、派生アレルderivedreads[i]、およびアンカーポピュレーションにおける頻度frequencies[i]があります。
