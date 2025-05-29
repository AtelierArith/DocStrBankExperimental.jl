```
haskey(sc,k)
```

SortedDict、SortedMultiDict、またはSortedSet `sc` に対してキー `k` が存在する場合は true を返します。SortedSet の場合、`haskey(sc,k)` は `in(k,sc)` の同義語です。SortedDict と SortedMultiDict の場合、`haskey(sc,k)` は `in(k,keys(sc))` と同等です。時間: O(*c* log *n*)
