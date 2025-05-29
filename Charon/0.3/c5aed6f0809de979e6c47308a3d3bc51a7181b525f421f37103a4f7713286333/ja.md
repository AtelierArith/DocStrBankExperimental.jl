```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, sedimentdata::AbstractString, frequencies::AbstractString, derivedreads::AbstractVector{<:Integer}, frequencies::AbstractVector{<:Real}; messages::Integer=nsteps÷100, scalingmessages::Bool=true, headersedimentdata::Union{Nothing, Bool}, headerfrequencies::Union{Nothing, Bool})
```

sedimentdataはCSVファイルへのパスであり、最初の列は派生リードで、2番目の列はカバレッジです。frequenciesは、アンカーポピュレーションの周波数を含む1列のCSVファイルへのパスです。両方のファイルの行数は同じである必要があります。
