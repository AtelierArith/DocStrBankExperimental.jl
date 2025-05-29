```
significant_transitions(res::ChangesResults, signif::Significance)
```

`res`を使用して`signif`によって説明された方法で重要な遷移を推定します。`flags`を返します。これは、`res`に格納されている変更と同じサイズのブール行列です（通常、`res.x_change`フィールドに格納されています）。`flags`は、`res`の変更メトリックが重要と見なされる場所で`true`になります。
