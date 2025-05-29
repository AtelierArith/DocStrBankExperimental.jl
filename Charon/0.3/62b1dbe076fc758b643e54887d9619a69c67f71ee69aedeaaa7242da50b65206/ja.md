```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, sedimentdata::DataFrame, frequencies::DataFrame; messages::Integer=nsteps÷100, scalingmessages::Bool=true)
```

sedimentdataはDataFrameへのパスであり、最初の列は派生リードで、2番目の列はカバレッジです。frequenciesは1列のDataFrameで、アンカーポピュレーションの頻度を含んでいます。両方のファイルの行数は同じである必要があります。
