```julia
calcPPE(var; ...)
calcPPE(var, varType; ppeType, solveKey, ppeKey)

```

分散因子グラフ内の変数の完全な周辺信念推定に基づくParametricPointEstimatesを取得します。特定の変数に対して新しいParametric Point Estimatesを計算します。

DevNotes

  * TODO マニフォールドサブグループの更新。
  * TODO AMP3Dの後に標準化

関連

[`getPPE`](@ref), [`setPPE!`](@ref), [`getVariablePPE`](@ref)
