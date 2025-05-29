```
Rank(taxon::Taxon)
```

Return `CanonicalRank` made from `rank(taxon)` if `rank(taxon)` is in `CanonicalRanks`. Return `UnCanonicalRank(rank)` if not. `CanonicalRank(taxon)` can be used for `isless` comparison.
