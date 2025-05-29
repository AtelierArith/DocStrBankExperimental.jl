```julia
deepcopyGraph(, sourceDFG; ...)
deepcopyGraph(, sourceDFG, variableLabels; ...)
deepcopyGraph(
    ,
    sourceDFG,
    variableLabels,
    factorLabels;
    sessionId,
    kwargs...
)

```

ノードを1つのグラフから新しいグラフにディープコピーを作成してコピーします。詳細については[`copyGraph!`](@ref)を参照してください。関連:

  * [`deepcopyGraph!`](@ref)
  * [`buildSubgraph`](@ref)
  * [`getNeighborhood`](@ref)
  * [`mergeGraph!`](@ref)
