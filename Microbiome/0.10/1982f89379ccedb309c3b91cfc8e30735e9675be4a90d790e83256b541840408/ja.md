```
prevalence_filter(comm::AbstractAbundanceTable; minabundance=0.0; minprevalence=0.05, renorm=false)
```

`minprevalence` よりも低い有病率の特徴が削除されたフィルタリングされた `CommunityProfile` を返します。デフォルトでは、特徴は > 0 の場合に「存在する」と見なされますが、`minabundance` を設定することで変更できます。

オプションで、低有病率の特徴が削除された後に相対的な豊富さを計算するには、`renorm = true` を設定します。
