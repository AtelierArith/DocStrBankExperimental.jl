```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, coverages::AbstractVector{<:Integer}, derivedreads::AbstractVector{<:Integer}, frequencies::AbstractVector{<:Real}, messages::Integer=nsteps÷100, scalingmessages::Bool=true)
```

coverages[i] はカバレッジ、derivedreads[i] は派生リードの数、frequencies[i] はローカス i におけるアンカーポピュレーションでの派生アレルの頻度です。
