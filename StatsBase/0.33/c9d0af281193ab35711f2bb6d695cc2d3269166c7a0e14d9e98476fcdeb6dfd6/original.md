```
denserank(x; lt=isless, by=identity, rev::Bool=false, ...)
```

Return the [dense ranking](http://en.wikipedia.org/wiki/Ranking#Dense_ranking_.28.221223.22_ranking.29) ("1223" ranking) of an array. Supports the same keyword arguments as the `sort` function. Equal items receive the same rank, and the next subsequent rank is assigned with no gap. Missing values are assigned rank `missing`.
