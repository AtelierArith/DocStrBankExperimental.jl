```julia
deepcopyGraph!(destDFG, sourceDFG; ...)
deepcopyGraph!(destDFG, sourceDFG, variableLabels; ...)
deepcopyGraph!(
    destDFG,
    sourceDFG,
    variableLabels,
    factorLabels;
    kwargs...
)

```

ノードを1つのグラフから別のグラフにディープコピーを作成してコピーします。詳細については[`copyGraph!`](@ref)を参照してください。関連:

  * [`deepcopyGraph`](@ref)
  * [`buildSubgraph`](@ref)
  * [`getNeighborhood`](@ref)
  * [`mergeGraph!`](@ref)
