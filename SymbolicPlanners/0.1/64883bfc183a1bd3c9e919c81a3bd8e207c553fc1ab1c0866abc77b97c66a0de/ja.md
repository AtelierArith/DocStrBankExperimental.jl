```
MinActionCosts(terms, costs)
MinActionCosts(terms, actions, costs)
```

[`Goal`](@ref) 仕様では、各アクションに特定のコストがあり、ゴール式は `terms` の論理積です。この仕様で呼び出されたプランナーは、返される [`Solution`](@ref) の総アクションコストを最小化しようとします。

コストは、アクション名（`Symbol` として指定）から `Real` へのマッピングとして提供できます。これにより、各リフトされたアクションに関連するコストが設定されます。あるいは、コストはグラウンドアクション `Term` から `Real` へのマッピングとして提供できます。マッピングは、`NamedTuple` または `Dictionary` として直接提供するか、`actions` と対応する `costs` のリストとして提供できます。
