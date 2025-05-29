```
MCMCsampler(nchains::Integer, nsteps::Integer, prioronn::DiscreteUnivariateDistribution, prioronτCτA::ContinuousMultivariateDistribution, prioronϵ::ContinuousUnivariateDistribution, dicefile::AbstractString, messages::Integer=nsteps÷100, scalingmessages::Bool=true)
```

dicefileはDICE 2-pop形式の(zipped) CSVファイルです：正確に4つの列を含む必要があります。最初の列には祖先リードの数が含まれ、2番目の列には派生リードの数が含まれ、3番目の列にはアンカーポピュレーションにおける派生アレルの頻度が含まれ、4番目の列にはこのデータの組み合わせを持つロキの数が含まれます。
