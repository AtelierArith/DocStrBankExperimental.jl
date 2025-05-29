```
haskey(sc,k)
```

Returns true if key `k` is present for SortedDict, SortedMultiDict or SortedSet `sc`. For SortedSet, `haskey(sc,k)` is a synonym for `in(k,sc)`. For SortedDict and SortedMultiDict, `haskey(sc,k)` is equivalent to `in(k,keys(sc))`. Time: O(*c* log *n*)
