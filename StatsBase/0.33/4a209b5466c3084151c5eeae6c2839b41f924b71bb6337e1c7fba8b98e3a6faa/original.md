```
ordinalrank(x; lt=isless, by=identity, rev::Bool=false, ...)
```

Return the [ordinal ranking](https://en.wikipedia.org/wiki/Ranking#Ordinal_ranking_.28.221234.22_ranking.29) ("1234" ranking) of an array. Supports the same keyword arguments as the `sort` function. All items in `x` are given distinct, successive ranks based on their position in the sorted vector. Missing values are assigned rank `missing`.
