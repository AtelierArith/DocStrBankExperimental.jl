```julia
setPPE!(variable)
setPPE!(variable, solveKey)
setPPE!(variable, solveKey, ppeType)
setPPE!(variable, solveKey, ppeType, newPPEVal)

```

変数のために新しいPPE推定値を計算し、いくつかの分散因子グラフから設定します。

DevNotes

  * TODO 解決キーは、1つだけを更新したい場合に必要かもしれません。
  * TODO より適切な名前を考慮してください。
  * :default=>variableNodeData が :default=>MeanMaxPPE と一緒に使われるのは理にかなっていると思います。

エイリアス

  * `setVariablePosteriorEstimates!`

DevNotes:

JT - TODO サブFGがクラウドにある場合や別のFGからのものである場合、全体の変数を1つのフィールドのために更新するのは無駄に感じます。現在、mergeUpdateVariableSolverData()を見つけましたが、updatePointParametricEst(dfg, variable, solverkey)のようなセッターを使用するのが便利かもしれません。これは正しい場所ではないかもしれません。コメントを外すと: $if (subfg <: InMemoryDFGTypes)   updateVariable!(subfg, var) end$

関連

[`calcPPE`](@ref), getVariablePPE, (updatePPE! ?)
