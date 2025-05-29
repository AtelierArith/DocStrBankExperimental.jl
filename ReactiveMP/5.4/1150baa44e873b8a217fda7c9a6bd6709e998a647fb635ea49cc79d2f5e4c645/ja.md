`FlowMeta`構造体は`Flow`ファクターノードのメタデータを含んでいます。より具体的には、`Flow`ファクターノードのモデルを含んでいます。`FlowMeta`構造体は`FlowMeta(model)`として構築できます。フローモデルがコンパイルされていることを確認してください。

`FlowMeta`構造体は`Flow`ファクターノードに必要であり、Flowノードと共に次のように含めることができます：`y ~ Flow(x) where { meta = FlowMeta(...) }`
