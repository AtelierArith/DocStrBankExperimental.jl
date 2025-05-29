```
ClassTransformer(classifier; kwargs...)
```

このトランスフォーマーは、`ACC`、`PACC`、`CC`、`PCC`、および `SLD` で使用される分類ベースの特徴変換を提供します。

**キーワード引数**

  * `is_probabilistic = false` 後方予測を使用するかどうか。
  * `fit_classifier = true` 指定された `classifier` をフィットさせるかどうか。
