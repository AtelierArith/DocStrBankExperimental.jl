```julia
copyGraph!(destDFG, sourceDFG; ...)
copyGraph!(destDFG, sourceDFG, variableLabels; ...)
copyGraph!(
    destDFG,
    sourceDFG,
    variableLabels,
    factorLabels;
    copyGraphMetadata,
    overwriteDest,
    deepcopyNodes,
    verbose,
    showprogress
)

```

グラフから別のグラフにノードをコピーするための一般的な関数です。パフォーマンスのために特化した実装でオーバーライドされています。孤立したファクターは追加されず、verboseが有効な場合は警告が表示されます。`overwriteDest`を設定すると、宛先DFG内の既存の変数やファクターを上書きします。注意: copyGraphMetadataはまだサポートされていません。関連:

  * [`deepcopyGraph`](@ref)
  * [`deepcopyGraph!`](@ref)
  * [`buildSubgraph`](@ref)
  * [`getNeighborhood`](@ref)
  * [`mergeGraph!`](@ref)
