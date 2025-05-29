```julia
buildSubgraph(, dfg, variableFactorLabels; ...)
buildSubgraph(
    ,
    dfg,
    variableFactorLabels,
    distance;
    solvable,
    sessionId,
    kwargs...
)

```

DFGから変数と因子のリスト、およびオプションの距離を指定して深いサブグラフコピーを構築します。注意: 孤立した因子（サブグラフがすべての関連変数を含まない場合）は返されません。関連:

  * [`copyGraph!`](@ref)
  * [`getNeighborhood`](@ref)
  * [`deepcopyGraph`](@ref)
  * [`mergeGraph!`](@ref)

開発ノート

  * バルク対ノードごとの: ラベルのリストがコンパイルされ、サブグラフが一括でコピーされます。
