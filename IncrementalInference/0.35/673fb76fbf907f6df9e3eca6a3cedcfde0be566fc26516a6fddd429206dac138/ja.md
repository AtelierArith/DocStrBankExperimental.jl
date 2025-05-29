```julia
getCliqVarSolveOrderUp(cliq)

```

`cliq`内のミニバッチギブス反復に必要な変数IDの順序リストを決定して返します。

ノート

  * シングルトン因子（事前および上メッセージ）はリストの後ろに
  * リストの前に関連する因子変数の最小数
  * mcmcIterationIdsOrderedと同じ
