```
heatmap(expl::Explanation)
heatmap(expl::Explanation, pipeline)
heatmap(expl::Explanation, image)   
heatmap(expl::Explanation, image, pipeline)
```

XAIBaseからの`Explanation`をビジョンヒートマップとして視覚化します。`explanation.val`のためにWHCN規約（幅、高さ、チャネル、バッチ次元）を仮定します。これは、与えられたタイプの説明に対してデフォルトのヒートマッピングスタイルを使用します。
