```
`FoldDetectEvent`
```

このイベントは、継続曲線の接線ベクトルのp成分に基づいてFoldポイントの検出を実装しています。これは、継続アルゴリズムとして`PALC(tangent = Bordered())`と連携して動作するように設計されています。使用するには、`continuation`に`event = FoldDetectEvent`を渡してください。
