```
heatmap(input::AbstractArray, analyzer::AbstractXAIMethod)
heatmap(input::AbstractArray, analyzer::AbstractXAIMethod, image)
```

与えられた `input` に対して XAI メソッド `analyzer` を使用して `Explanation` を計算し、それをビジョンヒートマップとして視覚化します。これは、与えられたタイプの説明に対してデフォルトのヒートマッピングスタイルを使用します。
