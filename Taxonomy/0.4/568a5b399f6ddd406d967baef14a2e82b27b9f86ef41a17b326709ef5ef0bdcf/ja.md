```
Rank(taxon::Taxon)
```

`rank(taxon)` が `CanonicalRanks` に含まれている場合は、`rank(taxon)` から作成された `CanonicalRank` を返します。含まれていない場合は `UnCanonicalRank(rank)` を返します。`CanonicalRank(taxon)` は `isless` 比較に使用できます。
