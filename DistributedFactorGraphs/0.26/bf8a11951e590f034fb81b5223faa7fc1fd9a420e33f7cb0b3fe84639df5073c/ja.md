```julia
isFactor(dfg, sym)

```

`sym::Symbol`がグラフDFGの因子頂点を表すかどうかを返します。グラフに存在し、かつ因子であるかどうかをチェックします。（タイプのためにより迅速な方法を望む場合は、単にnode isa FactorComputeを実行してください。）
