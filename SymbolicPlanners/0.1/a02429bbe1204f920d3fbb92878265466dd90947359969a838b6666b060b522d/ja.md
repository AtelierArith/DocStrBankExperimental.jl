```
ExtraPerAgentActionCosts(spec::Specification, costs, [agent_arg_idx=1])
```

基盤となる `spec` にエージェントごとのアクションコストを追加するラッパーです。

コストは、最初のレベルがエージェント名（`Symbol` または `Const` として指定）を、2 番目のレベルがアクション名またはグラウンドアクション `Term` を `Real` にマッピングするネストされた辞書または名前付きタプルとして提供できます。
