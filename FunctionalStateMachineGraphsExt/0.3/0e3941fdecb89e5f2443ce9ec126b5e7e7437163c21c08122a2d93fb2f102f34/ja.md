```julia
histGraphStateMachineTransitions(
    stateVisits,
    allStates;
    maxpenwidth,
    minpenwidth
)

```

`Graphs.incdict`オブジェクトを作成し、渡されたパラメータの内容に従ってノード（状態）とエッジ（遷移）で populated します。

ノート：

  * 現在の実装では、重複する遷移を新しいエッジとして繰り返します。
