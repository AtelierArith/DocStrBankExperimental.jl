```julia
findVariableNearTimestamp(dfg, timest; ...)
findVariableNearTimestamp(
    dfg,
    timest,
    regexFilter;
    tags,
    solvable,
    warnDuplicate,
    number
)

```

デルタ時間ごとに最も近い変数ラベルを見つけて返します。関数は `regexFilter`、`tags`、および `solvable` でフィルタリングします。

ノート

  * `Vector{Tuple{Vector{Symbol}, Millisecond}}` を返します。

DevNotes:

  * TODO `number` は k-最近接マッチのために複数を返すことを許可するべきです。
  * 将来のバージョンでは、内部の `getVariable` 呼び出しに関して最適化が必要になる可能性があります。

      * すべての DFG フレーバー用の専用/効率的な `getVariableTimestamp` が必要かもしれません。

関連

ls, listVariables, findClosestTimestamp
