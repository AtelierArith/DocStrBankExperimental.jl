```
ExtraActionCosts(spec::Specification, costs)
ExtraActionCosts(spec::Specification, actions, costs)
```

基盤となる `spec` にアクション固有のコストを追加するラッパーです。

コストは、各リフトされたアクションに関連付けられたコストを持つように、アクション名（`Symbol` として指定）から `Real` へのマッピングとして提供できます。あるいは、コストは地上アクション `Term` から `Real` へのマッピングとして提供できます。マッピングは、`NamedTuple` または `Dictionary` として直接提供することも、`actions` と対応する `costs` のリストとして提供することもできます。
