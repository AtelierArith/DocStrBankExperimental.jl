```
`stop!(:: AbstractStopping; kwargs...)`
```

Stoppingを更新し、停止する必要がある場合は真のブール値を返します。

これは、アルゴリズムにおける`start!`と同じ目的を果たします。最適性に達したか、無限ループに陥ったかなど、アルゴリズムを停止するかどうかを教えてくれます。

関数`stop!`は次々に以下を呼び出します: `_domain_check`, `_optimality_check`, `_null_test`, `_unbounded_check!`, `_tired_check!`, `_resources_check!`, `_stalled_check!`, `_iteration_check!`, `_main_pb_check!`, `add_to_list!`

注意:

  * kwargsは`_optimality_check!`呼び出しに送信されます。
  * `listofstates != VoidListofStates`の場合、`add_to_list!`を呼び出します。
