```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, sedimentdata::AbstractString, frequencies::AbstractString, derivedreads::AbstractVector{<:Integer}, frequencies::AbstractVector{<:Real}; messages::Integer=nsteps÷100, scalingmessages::Bool=true, headersedimentdata::Union{Nothing, Bool}, headerfrequencies::Union{Nothing, Bool})
```

sedimentdata is a path to a CSV file, where the first column are the derived reads, and the second column are the coverages. frequencies is a path to a CSV file with one column, containing frequencies of the anchor population. The number of rows of both files should be the same. 
