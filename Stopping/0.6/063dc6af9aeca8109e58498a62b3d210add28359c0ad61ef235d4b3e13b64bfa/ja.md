```
`cheap_stop!(:: AbstractStopping; kwargs...)`
```

Stoppingを更新し、停止する必要がある場合は真のブール値を返します。

これは`stop!`と同じ目的を果たしますが、潜在的に高価なチェックを回避します。もはやState内の`x`や`res`を参照せず、`main_stp`に対するチェックも行いません。メタ内の更新されたエントリのみをチェックします。

関数`cheap_stop!`は次の関数を順次呼び出します: `_null_test`, `_unbounded_check!`, `_tired_check!`, `_resources_check!`, `_stalled_check!`, `_iteration_check!`, `add_to_list!`

注意:

  * kwargsは`_optimality_check!`呼び出しに送信されます。
  * `listofstates != VoidListofStates`の場合、`add_to_list!`を呼び出します。
